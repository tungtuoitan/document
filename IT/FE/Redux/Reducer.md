
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
