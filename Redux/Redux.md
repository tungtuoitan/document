# 1.TỔNG QUAN

## redux là gì?

- là pattern và thư viện dùng để quản lí/update state
- là 1 sự triển khai của kiến trúc Flux
- là 1 thư viện JS độc lập

## Hệ sinh thái quanh redux

- React-redux
- Redux-toolkit
- Redux-Devtool Extension

## Lí do ra đời?\*

- được tạo ra để giải quyết các hạn chế của event-trigger-base state management

## đặc điểm của redux

- hoạt động update state có thể dự đoán được (Predictable)
- one-way data flow

## Tradeoff của redux

- phải code nhiều
- code dài dòng, lê thê
- nhiều khái niệm mới cần học
- phải tuân thủ các hạn chế\*

## Khi nào nên dùng redux?

- có 1 lượng lớn state dùng ở nhiều nơi trong app
- state cần update thường xuyên theo thời gian
- logic update phức tạp
- medium/large size codebase và có nhiều dev

# 2.REDUCER

## Rule của reducer

- chỉ được tính toán new state từ: current state và action
- không được phép mutate current state, mà phải dùng immutable update

## lợi ích của rule

- rule1 >> predictable, có nghĩa là code dễ đọc, dễ viết tests
- rule immutable update:
  ( ít gây ra bug
- làm nền tảng cho các tính năng khác hoạt động (vd devtool)
  )

## Nguồn gốc tên Reducer

- Bắt nguồn từ Array.reduce(callback, initialState)
- logic của hàm Reducer giống hệt logic của hàm callback trong reduce()

## Khi state là nested object

- việc immutable nested object là rất dễ sai, khó viết
- [](#tại-sao-immutable-update-logic-lại-khó-viết-khi-state-là-nested-object)

## Lỗi phổ biến trong immutable update

- chỉ shallow copy 1 level
  function updateNestedState(state, action) {
  // Problem: this only does a shallow copy!
  let newState = { ...state }
  ...
  }
- dùng insert, remove cho current state
  function insertItem(array, action) {
  return [
  ...array.slice(0, action.index),
  action.item,
  ...array.slice(action.index)
  ]
  }

# CÁC IMMUTABLE UPDATE PATTERN PHỔ BIẾN

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
# 3.HOẠT ĐỘNG CỦA REDUX

## Hoạt động khởi tạo ban đầu

1. Redux store được tạo ra từ hàm root reducer
2. store gọi root reducer 1 lần duy nhất, để lấy initial state
3. UI được render lần đầu cũng dựa vào initial state

## Hoạt động update

1. user click
2. dispatch(action) đến store
3. store thực thi reducer tương ứng
4. update state
5. store thông báo cho các component là vừa có update
6. các component sẽ kiểm tra xem state của mình có bị thay đổi không? nếu có thì re-render UI

# 4.IMMUTABLE UPDATE

## Tại sao không được biến đổi state trực tiếp ?

- vì nó sẽ gây ra bug (như việc state update nhưng UI thì không)
- vì redux dùng shallow quality checking, chứ k phải deep quality checking
- khó viết tests
- code khó đọc
- k thể sử dụng tính năng “time-travel debuggin”
- đi ngược lại tinh thần và pattern mà redux sử dụng

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

# 5.KHÁI NIỆM

## Dispatch

- là hàm truyền action đến store

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

# 6.ANOTHER

## Khởi tạo store

- configureStore({reducer: reducer})

## Chức năng của store

- lấy current state: store.getState()
- update state (bằng cách thực thi Reducer)
