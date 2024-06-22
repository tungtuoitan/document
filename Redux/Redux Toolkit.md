# 1.TỔNG QUAN
## Lợi ích so với Redux
- cho phép viết mutable logic trực tiếp trong reducer (chỉ được viết trong createSlice và createReducer)
- Code ít hơn

# 2.DÙNG RTK
## Tạo store
configureStoreimport { configureStore } from '@reduxjs/toolkit'
import counterReducer from '../features/counter/counterSlice'

export default configureStore({
  reducer: {
    counter: counterReducer
  }
})





# 3.KHÁI NIỆM
## Slice
- là 1 tập hợp gồm state, reducers và action tương ứng với 1 feature cụ thể của app
(tên "slice" đến từ việc chia root state thành từng slice)

## combineReducer()
- dùng để kết hợp các reducer lại thành root reducer, để truyền vào configureStore

## createSlice()
- 
# 4.ANOTHER
## Tại sao  có thể viết mutable logic trong reducer ?
- RTK dùng thư viện Immer để chuyển code mutable logic thành immutable logic

## chỉ 