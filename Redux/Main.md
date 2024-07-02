# **1: Tổng quan**

<!-- TỔNG QUAN -->

## redux là gì?

- là pattern và cũng là thư viện dùng để quản lí state

## Hệ sinh thái quanh redux ??

- Redux
- React-redux
- Redux-toolkit
- Redux-Devtool Extension
- Redux thunk
- Redux saga
- redux persist
- redux logger
  redux-immutable-state-invariant (phát hiện mutate state code)
- Immer
- ducks-modular-redux

## Điểm mạnh của redux ?

- dễ dàng truy cập state ở mọi nơi
<!-- vì tập trung state vào 1 chỗ duy nhất -->
- tối ưu hiệu suất
<!-- vì redux bỏ qua re-render khi state không thay đổi -->
- code dễ hiểu,
<!-- vì nguyên lí predictable và one-way data flow-->
- dễ debug,
<!-- vì predictable và tính năng time travel debugging -->
- dễ test
<!-- vì dùng pure function, và mỗi function chỉ thực hiện 1 chức năng -->
- Tích hợp tốt với React,
<!--  vì được thiết kế để làm việc với React -->
- cộng đồng support lớn

- chạy trên nhiều môi trường khác nhau
<!-- client, server, native -->

## Điểm yếu của redux ?

- code dài dòng, lê thê
<!-- vì nhiều boilerplate code -->
- nhiều khái niệm và best pratice cần học
<!-- vd: store, reducer, selector, ... -->
- chỉ phù hợp cho app vừa/lớn
<!-- vì nếu data flow k phức tạp thì dùng useContext là đã đủ -->
- bắt tuân theo những hạn chế nhất định ??

## Khi nào nên dùng redux ?

- app vừa hoặc lớn, nhiều dev làm, hoặc logic update state phức tạp
<!-- vì lúc này sẽ cần khả năng quản lí state dễ dàng và code dễ đọc của redux -->

## Nguyên tắc redux ?

- 1 store cho toàn bộ app
  <!-- để có được các lợi ích: dễ tạo universal app, data flow dễ hiểu, dễ debug, dễ test, dễ quản lí state (universal app là app có thể chạy trên cả client và server), dễ dàng reset lại web mà k mất trạng thái (vì có thể lưu lại trạng thái toàn bộ trang web dễ dàng), dễ triển khai tính năng hơn (vd: undo/redo) -->
- update state phải thông qua dispatch action
<!-- để có được data flow dễ hiểu, dễ debug -->
- pure reducer
<!-- để dễ hiểu, dễ debug -->
- immutable update
  <!-- vì immutable update giúp cho hoạt động quality check được tối ưu, -->

## 2 cách dispatch action đến store

- dùng props.dispatch
- dùng hàm custom dispatch trong mapDispatchToProps

## redux xác định state thay đổi bằng cách nào ?

- nguyên tắc immutable update + [shallow comparision]

## Khi nào component re-render ?

- khi có bất kì field nào trong return object của mapStateToProps() thay đổi thì sẽ re-render
<!-- - mặc định, React Redux sẽ check xem object trả về từ mapStateToProps có khác nhau hay không, dùng "===" trong mỗi field của return object
- nếu bất kì field nào thay đổi thì comopnent re-render -->

# Cách tối ưu hóa performance trong Redux ?

# **2: Các hoạt động của redux**

## update state

- user click
- dispatch action
<!-- (bằng các hàm trong mapDispatch hoặc props.dispatch) -->
- reducer() tương ứng run để update state
- toàn bộ mapStateToProps re-run
- Redux shallow quality check xem state có "thay đổi" không?
- component re-render

## data flow từ store đến component

store.state --> mapStateToProps() --> props --> component

## cách redux trigger re-render

- redux luôn giả sử component là pure
- redux so sánh return value của mapStateToProps trước và sau, xem có "thay đổi" hay không,
- nếu có thì re-render
- Redux dùng [shalow comparision] để so sánh

## sử dụng Redux với React

- định nghĩa reducer
- compine reducer (nếu cần)
- tạo store
- cung cấp store cho app
<!-- <Provider store={store}> -->

- kết nối store và component với nhau
<!--

* mapStateToProps(): lấy ra data mà component cần từ store
* mapDispatchToProps(): để viết custom dispatch function và truyền vào component để sử dụng -->

# **3: Thành phần chính**

## mapStateToProps() / mapState

### chức năng

- lấy ra data mà component cần
- luôn trả về data mới nhất
<!-- - nhận vào toàn bộ store, và trả về 1 object chứa data -->

#### làm sao mapState có thể luôn luôn trả về data mới ?

- toàn bộ mapState luôn luôn chạy lại mỗi khi store.state hoặc ownProps "thay đổi"
<!-- (tức mỗi lần store thay đổi, toàn bộ mapStateToProps đều chạy) -->

### syntax:

- function mapStateToProps(state, ownProps?)

### cách dùng:

- truyền mapState vào connect()
<!--SOURCE: https://react-redux.js.org/using-react-redux/connect-mapstate -->

### mapState khác gì so với việc "return state.someSlice ?

- mapState có thể làm được nhiều việc như:
- đặt lại tên cho state
- kết hợp nhiều data từ store trước khi trả về
- biến đổi data

### như thế nào là hàm mapState tốt ?

- phải rất "nhẹ",
<!-- vì mỗi khi state của store thay đổi, tất cả hàm mapState đều chạy lại -->
- pure
<!-- vì sao: tự giải thích thì pure để dễ test và predictable -->
- synchronous
<!-- vì sao?: tự giải thích thì để đảm bảo perfornamce tốt, vì mỗi khi state của store thay đổi thì mọi hàm mapState đều chạy lại -->

- tránh dùng [hàm tạo new reference]
  <!-- vì trả về new reference sẽ kích hoạt re-render, gây performance problem, -->
- Hạn chế dùng ownProps
<!-- vì khi dùng thì mapStateToProps() sẽ chạy nhiều hơn, do ownProps thay đổi thì mapState cũng sẽ chạy lại -->

### làm sao để giữ cho mapState nhẹ ?

- cố xử lí logic biến đổi data phức tạp ở trong reducer, action creator hoặc trong component
- khi logic biến đổi data cần nằm trong mapState(), thì hãy dùng memoized selector function để đảm bảo transformation chỉ chạy khi input thay đổi
<!-- https://redux.js.org/recipes/computing-derived-data#creating-a-memoized-selector -->

- tránh dùng các phương thức toJS(), toObject(), toArray() trong thư viện immutable.js và ...
<!-- tham khảo thêm các link ở cuối trang này: https://react-redux.js.org/using-react-redux/connect-mapstate#mapstatetoprops-and-performance -->

### các tình huống đặc biệt làm cho mapState re-render ?

<!-- https://react-redux.js.org/using-react-redux/connect-mapstate#the-number-of-declared-arguments-affects-behavior -->

## connect()

function connect(mapStateToProps?, mapDispatchToProps?, mergeProps?, options?)

### chức năng của connect

- kết nối component với Redux store, để có thể truyền data cho component từ store và dispatch action từ component đến store

### return value

- trả về 1 component mới, wrap component mà ta truyền vào

### Paremeter

- mapStateToProps: khi không muốn kết nối component với store, thì ta truyền vào null/undefined
- ta có thể định nghĩa mapState/mapDispatch như là factory function
<!-- xem thêm: https://react-redux.js.org/api/connect#factory-functions -->
- mapDispatch: khi không truyền vào, thì component mặc định sẽ nhận hàm store.dispatch()

## mapDispatchToProps / mapDispatch

### chức năng của mapDispatch()

- tạo ra các hàm dispatch custom
- cho phép dispatch đến store bằng các hàm dispatch custom
  <!-- bằng cách: "truyền các hàm dispatch custom vào trong component dưới dạng props" -->

  <!-- ví dụ hàm dispatch custom:
  const mapDispatchToProps = (dispatch) => ({
    dispatchSomeAction: () => dispatch(someActionCreator())
  }); -->

### lợi lích của việc dùng mapDispatch() so với dùng dispatch() mặc định ?

- code trực quan hơn
<!-- vì việc dispatch 1 action, và để redux xử lí data là kịch bản rất dễ hiểu, -->
- cho phép truyền hàm dispatch action xuống child component

### 2 loại MapDispatch

[](./bonus/2LoaiMapDispatch.md)

### các vấn đề phổ biến

<!-- https://react-redux.js.org/using-react-redux/connect-mapdispatch#defining-mapdispatchtoprops-as-an-object -->

# **4: Phụ**

### các hàm tạo new reference phổ biến:

someArray.map() , someArray.filter, array.concat(), array.slice(), Object.assign()., {...oldState, ...newData}

## bindActionCreators()

bindActionCreators(actionCreators, dispatch)

- vẫn còn hoạt động, nhưng hầu như không dùng tới

### chức năng

- chuyển object có action creator thành object với same key, nhưng mỗi action creator sẽ wrap 1 dispatch để ...

## action creator

### chức năng

- tạo ra "dynamic" action và dispatch đến store 1 cách dễ dàng
- thực hiện logic bất đồng bộ

### lợi ích của việc dùng action creator so với viết action trực tiếp ?

- giảm boilerplate
  <!-- vì ta không cần phải viết lại cấu trúc action, payload mỗi lần dùng, mà chỉ cần gọi actionCreator() -->
- refactor dễ dàng
  <!-- vì khi refactor, ta chỉ cần chỉnh sửa action creator -->
- code dễ hiểu ??
<!-- vì tách biệt hành động tạo action và gửi action ?? -->

## điều gì xảy ra khi ta không tuân thủ nguyên tắc immutable update ?

- khi không tuân thủ immutable update thì component sẽ không re-render khi state thay đổi
  <!-- vì Redux "không thấy được" sự thay đổi -->
  <!-- Redux không thấy được sự thay đổi vì::
- shallow comparison trong redux chỉ chính xác khi ta tuân thủ nguyên tắc immutable update
- khi ta k tuân thủ, mà biến đổi trực tiếp (vd: state.a = 'xyz') thì object cũ và object mới vẫn có địa chỉ giống nhau, mặc dù bên trong object đã thay đổi -->

### shallow comparision

- là so sánh reference, tức địa chỉ của 2 object
- redux dùng strict equality ("===") và strict equality là 1 loại shallow comparision

## troubleshooting

- component không re-render khi update state
<!-- vì mapStateToProps trả về mutated Object, do khi mutate trực tiếp trong object thì React Redux không phát hiện được là object đó thay đổi, do react redux dùng "===" để so sánh -->

## lưu ý:

- khi nào dev có vấn đề với state management thì mới thấy được lợi ích của redux

- redux là 1 sự triển khai của kiến trúc Flux
- redux là 1 thư viện JS độc lập

## boilerplate code

- là phần code được tái sử dụng rất nhiều lần mà hầu như không có thay đổi

## best pratice là gì?

- là cách làm tốt nhất
<!-- https://toidicodedao.com/2018/07/10/hoc-best-practice-programming/ -->

## pattern

- là giải pháp để giải quyết 1 vấn đề cụ thể, ở design level
- nó không phải code, mà là text mô tả <!-- source: https://www.freecodecamp.org/news/the-basic-design-patterns-all-developers-need-to-know/ -->

## Lí do redux ra đời?

- được tạo ra để giải quyết các hạn chế của event-trigger-base state management

## tại sao immutable update logic lại khó viết khi state là nested object?

vì nguyên tắc của immutable update là ta phải copy lại từng nesting object
vì thế, khi state là nest object phức tạp thì rất dễ viết sai

Ví dụ:
immutable logic:
function handwrittenReducer(state, action) {
return {
...state,
first: {
...state.first,
second: {
...state.first.second,
[action.someId]: {
...state.first.second[action.someId],
fourth: action.someValue
}
}
}
}

mutable logic (with RTK)
function reducerWithImmer(state, action) {
state.first.second[action.someId].fourth = action.someValue
}

ta chỉ có thể viết mutate logic trong createSlice và createReducer, vì chỉ ở trong này thì mới có Immer

## Dispatch

- là hàm truyền action đến store

## immutability (a)

- là tính bất biến

## immutable update

- là update state bằng cách:
- tạo ra copy state
- update trên copy state

## Action creator

- là hàm đơn giản, trả về đối tượng action

## Action

- là đối tượng Js, dùng để truyền payload đến Reducer tương ứng để update state

## Selector

- là 1 hàm để lấy 1 mẫu data cụ thể trong root state

## tại sao phải dùng selector mà không lấy data trực tiếp từ state

- để tái sử dụng code, khi mẫu data đó được lấy nhiều lần

## one-way data flow

- là 1 loại quan hệ giữa: UI / action / state
- cụ thể:
- UI phụ thuộc vào state, state thay đổi thì UI re-render
- khi có action, thì state update và UI sẽ re-render dựa trên new state

## Bên trong Action gồm thuộc tính gì?

- type: là string, có dạng abc/xyz
- payload: chứa data

## Non serializable value

- là các giá trị không thể chuyển sang JSON 1 cách an toàn và đáng tin cậy
- ví dụ các giá trị non-serializable: function, DOM element, class instance

## immutable update ở ngoài reducer

- khi new state được tính toán bên ngoài reducer, ta cũng phải tuân thủ nguyên tắc immutable update
<!-- ...Most Redux users realize they have to follow the rules inside a reducer, but it's not obvious that you also have to do this if the new state is calculated outside the reducer... trong https://redux.js.org/style-guide/ -->

# **5: Style Guide**

## Rules 1: Enssential

- không mutate state
<!-- vì nó làm hoạt động re-render không còn chính xác -->
- reducer phải pure và không được dùng các hàm tạo random value (Date.now(), Math.random()...)
<!-- vì như vậy thì reducer mới đạt tính predictable -->
- không dùng [non-serializable value] trong state / action
  điều này đảm bảo việc debug và Redux devtool, và hoạt động update UI hoạt động tốt

- ngoại lệ: ta có thể dùng [non-serializable value] trong action nếu ta có dùng middle-ware như redux-thunk, redux-promise...
- 1 store cho 1 app

## Rules 2: Strongly recommended

- dùng RTK
    <!-- vì nó có các hàm best practice, hàm setup store để phát hiện mutation và cho phép Redux DevTool Extension, cho phép viết "mutable update code" -->

- dùng Immer để viết "mutable code" khi không dùng RTK (khi dùng RTK thì Immer đã được tích hợp sẵn)
- cấu trúc file: có feature folder, và mỗi feature có 1 feature folder tương ứng, trong đó có 1 slice file (duck pattern)
  <!-- vì với cấu trúc cũ: 3 folder: action folder, reducer folder... sẽ gây khó khăn khi tìm kiếm file -->
  <!--
  Ví dụ:
  /src
    index.tsx: Entry point file that renders the React component tree
    /app
      store.ts: store setup
      rootReducer.ts: root reducer (optional)
      App.tsx: root React component
    /common: hooks, generic components, utils, etc
    /features: contains all "feature folders"
    /todos: a single feature folder
      todosSlice.ts: Redux reducer logic and associated actions
      Todos.tsx: a React component -->

- cố dồn hết logic vào reducer
<!--

* để cho dễ test (vì reducer luôn là pure function, trong khi onClick có thể k pure),
* dễ dùng time-travel debugging
* tránh mutation và bug: vì khi tính toán new state ở ngoài reducer thì ta cũng phải tuân thủ nguyên tắc "immutable update" vì [](#immutable-update-ở-ngoài-reducer)
* time-travel debugging hỗ trợ fix bug trong reducer rất tốt
* tập trung logic vào 1 chỗ sẽ dễ tìm kiếm -->

- Reducer nên "kiểm soát" state shape của nó, tức là:
<!--

* mỗi reducer tương ứng với 1 slice
* tránh dùng blind spread/returns trong reducer (vd: return action.payload, return {...state, ...action.payload}) vì như vậy thì cấu trúc của state sẽ phụ thuộc vào action, và điều này dễ dẫn đến bug khi nội dung action không chính xác
  ** việc dùng return action.payoad sẽ an toàn hơn khi ta biết type của action (vd: PayloadAction<User>)
  ** việc dùng spread return sẽ thích hợp cho 1 vài kịch bản: như edit data trong form -->

- Tổ chức state structure theo data type, chứ k phải component

<!-- * tức là nên phân thành các slice dựa theo loại data như: {auth, posts, users, ui} thay vì theo loại UI {loginScreen, userList, postList} vì store.state là của chung cho toàn bộ màn hình, mọi UI, và 1 data được nhiều component khác nhau sử dụng, -->

- logic xử lí của reducer nên phụ thuộc vào cả 2 (action và current state) chứ không phải chỉ mỗi action

<!-- * vì viết reducer càng chặt chẽ thì càng ít lỗi và code dễ hiểu hơn
ví dụ:
import {
  FETCH_USER,
  // ...
} from './actions'

const IDLE_STATUS = 'idle';
const LOADING_STATUS = 'loading';
const SUCCESS_STATUS = 'success';
const FAILURE_STATUS = 'failure';

const fetchIdleUserReducer = (state, action) => {
  // state.status is "idle"
  switch (action.type) {
    case FETCH_USER:
      return {
        ...state,
        status: LOADING_STATUS
      }
    }
    default:
      return state;
  }
}

// ... other reducers

const fetchUserReducer = (state, action) => {
  switch (state.status) {
    case IDLE_STATUS:
      return fetchIdleUserReducer(state, action);
    case LOADING_STATUS:
      return fetchLoadingUserReducer(state, action);
    case SUCCESS_STATUS:
      return fetchSuccessUserReducer(state, action);
    case FAILURE_STATUS:
      return fetchFailureUserReducer(state, action);
    default:
      // this should never be reached
      return state;
  }
} -->

- Normalize complex nested state & relational state
  vì: state phức tạp, bị duplicate thì khó để update chính xác

* nest state làm cho reducer phức tạp hơn
* khi update nested state, thì có thể vô tình làm thay đổi reference, dẫn đến các re-render không cần thiết

## Nornalize state

- là quá trình cấu trúc state cho hiệu quả
- nó đảm bảo:

* mỗi data có nơi của nó
* hạn chế duplication
* giảm độ phức tạp
* cải thiện performance

<!-- https://blog.saeloun.com/2021/09/23/normalize-redux-state/ -->

## normalize state trong redux

- mỗi entity type sẽ được lưu trữ riêng biệt, để không còn nested object
- lưu 1 entity dưới dạng 1 object, với id là key
- tham chiếu đến entity khác bằng id, chứ không dùng nested object nữa

## Update nested object

- giữ cho đối tượng state luôn flattened, và tạo ra càng nhiều reducer càng tốt

## update 1 item trong Array

function updateObjectInArray(array, action) {
return array.map((item, index) => {
if (index !== action.index) {
// This isn't the item we care about - keep it as-is
return item
}

    // Otherwise, this is the one we want - return an updated value
    return {
      ...item,
      ...action.item
    }

})
}

## Insert item trong array

function insertItem(array, action) {
let newArray = array.slice()
newArray.splice(action.index, 0, action.item)
return newArray
}

## Remove item trong array

function removeItem(array, action) {
let newArray = array.slice()
newArray.splice(action.index, 1)
return newArray
}
function removeItem(array, action) {
return array.filter((item, index) => index !== action.index)
}

## Dùng thư viện để viết immutable update

- có nhiều thư viện dành cho việc này, tìm ở (the Immutable Data#Immutable Update Utilities section of the Redux Addons Catalog)

- Immer:
  var usersState = [{ name: 'John Doe', address: { city: 'London' } }]
  var newState = immer.produce(usersState, draftState => {
  draftState[0].name = 'Jon Doe'
  draftState[0].address.city = 'Paris'
  //nested update similar to mutable way
  })

- dot-prop-immutable
  state = dotProp.set(state, `todos.${index}.complete`, true)

- dùng RTK
