# **1.TỔNG QUAN**

## Lợi ích so với Redux

- Giảm boilerplate
<!-- nhờ builder callback, -->
- Cấu hình dễ dàng
  <!-- nhờ cung cấp các API mới như configStore, createReducer,... và mặc định đã có các package phổ biến như: Immer, redux-thunk, redux-query -->
- cho phép viết mutable logic trực tiếp trong reducer (chỉ được viết trong createSlice và createReducer)
<!-- nhờ Immer -->
- fetching và caching mạnh mẽ
<!-- nhờ RTK Query -->

## Cách khởi tạo React Redux (khuyến khích dùng)

- RTK + template với Vite
<!-- https://github.com/reduxjs/redux-templates -->
- NextJs with-redux template
<!-- https://github.com/vercel/next.js/tree/canary/examples/with-redux -->

# **2.Các Hàm phổ biến**

## configStore()

### chức năng:

- cấu hình Redux 1 cách nhanh chóng, cụ thể là:

* kết hợp các slice reducer thành root reducer (nhờ gọi combineReducer)
* thêm các middleware như thunk (nhờ gọi applyMiddleware)
* thêm Redux Devtool
* tạo ra redux store (dùng createStore())
* cho phép cấu hình dễ dàng hơn bằng việc cung cấp tên field (vd: nameField, preloadState,...) và hỗ trợ TS tốt hơn

### ví dụ:

<!--
configureStoreimport { configureStore } from '@reduxjs/toolkit'
import counterReducer from '../features/counter/counterSlice'

export default configureStore({
reducer: {
counter: counterReducer
}
}) -->

### more infor

<!-- https://redux-toolkit.js.org/api/configureStore -->

## createReducer()

### chức năng:

- tạo reducer dễ dàng, cụ thể là:

* hỗ trợ map action và reducer tương ứng
* cho phép viết "mutable" update
<!-- nhờ dùng Immer làm mặc định -->
* hỗ trợ TS tốt hơn, ít bug hơn, loại bỏ boilerplate
<!-- nhờ Builer callback thay thế cho switch case -->

### action matcher

- nếu có reducer khớp tuyệt đối với action đó, thì reducer sẽ được thực thi đầu tiên
- các matcher trả về true sẽ thực thi theo thứ tự được định nghĩa
- nếu có default case reducer, và khi k có reducer nào match, thì default reducer sẽ được thực thi
- nếu không có case hoặc reducer nào chạy, thì state value ban đầu sẽ được return, (tức không có thay đổi)

## builder callback

### builder.addCase()

- chức năng: thêm 1 reducer để xử lí 1 action cụ thể
- lưu ý: mọi .addCase() phải đứng trước .addMatcher và .addDefaultCase()

### addMatcher()

- chức năng: cho phép ta map action với nhiều reducer khác, thay vì 1 reducer chính
- nếu nhiều reducer match, thì các reducer sẽ được thực thi lần lượt

### addDefaultCase()

- thêm defaultCase, và defaultCase reducer sẽ được thực thi nếu không có reducer nào match

## createSlice()

### chức năng

- tạo state ban đầu
- tạo reducer
- tạo action creator và action type từ reducer và state
<!-- bằng cách dùng createAction và createReducer bên trong -->

## combineSlice()

### chức năng

- gộp các slice thành 1 reducer
- cho phép thêm reducer sau khi khởi tạo

# **4.Phụ**

## khi nào cần thêm slice Reducer sau khi khởi tạo store (hầu như không dùng)

- khi muốn thêm tính năng mới vào ứng dụng ??
- quản lí trạng thái của các module động ??

## Cách thêm slice Reducer sau khi khởi tạo store (không phổ biến)

### tạo hàm rootReducer ban đầu

const createRootReducer = (asyncReducers) => combineReducers({
user: userReducer, // reducers ban đầu
posts: postsReducer,
...asyncReducers // reducers được thêm động
});

### tạo store với rootReducer

const store = createStore(createRootReducer());
store.asyncReducers = {}; // Lưu trữ các reducers động

### viết hàm thêm reducer

const injectReducer = (key, asyncReducer) => {
store.asyncReducers[key] = asyncReducer; // Thêm reducer mới vào asyncReducers
store.replaceReducer(createRootReducer(store.asyncReducers)); // Cập nhật root reducer
};

## thunk middleware

## current() dùng để làm gì ?

- dùng để theo dõi value dễ hơn khi log value,
<!-- vì khi dùng Immer thì  value bị bọc trong Proxy, -->

## Slice

- là 1 tập hợp gồm state, reducers và action tương ứng với 1 feature cụ thể của app
  (tên "slice" đến từ việc chia root state thành từng slice)

## combineReducer()

- dùng để kết hợp các reducer lại thành root reducer, để truyền vào configureStore

## createAsyncThunk()

### chức năng

- cho phép logic bdb trong action creator

###

- tạo ra promise
- tạo ra thunk action creator

- chạy promise callback
- dispatch lifecycle action

## createSlice()

-

# **4.ANOTHER**

## tại sao lại không dispatch action luôn, mà phải dispatch action creator ?

- vì dùng action creator thì ta có thể truyền tham số vào, tạo ra các action động
- vì dùng action creator sẽ làm giảm boilerplate

## Tại sao có thể viết mutable logic trong reducer ?

- RTK dùng thư viện Immer để chuyển code mutable logic thành immutable logic
