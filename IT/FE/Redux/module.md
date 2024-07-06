
### các loại module phổ biến và chức năng

#### coreModule():

- xử lí nội bộ, (sử dụng core Redux, slice, reducers, asyncThunk...)
- core module nhận vào api, options và thực hiện 1 loạt các bước build
- mỗi bước build là 1 loạt các hàm, sau đó gán chúng vào api.util/api.InternalActions và truyền vào các bước build tiếp theo

##### các bước build

###### buildThunk

- tạo ra 1 loạt các thunk cho core module sử dụng, như:
  queryThunk
  mutationThunk
  patchedQueryData
  updateQueryData
  upsertQueryData
  prefetch
  buildMatchThunkActions

###### buildSlice

- api là 1 slice của store
- api có slice của riêng nó, được tạo ra ở bên trong
- các slice được tạo ra gồm:
- querySlice
- mutationSlice
- invalidationSlice
- subscriptionSlice
- internalSubcriptionSlice
- configSlice
- resetApiState được tạo ra ở đây, và được lưu vào api.util

##### buildMiddleware

- RTK Query có 1 loạt các middleware cài sẵn để _xử lí thêm_ các response

buildDevCheckHandler
`buildCacheCollectionHandler
`buildInvalidationByTagsHandler
`buildPollingHandler
`buildCacheLifecycleHandler
`buildQueryLifecycleHandler

##### buildSelector

- expose api và util

`buildQuerySelector
`buildMutationSelector
`selectInvalidatedBy
`selectCachedArgsForQuery

#### reactHookModule():

tạo ra reactHook từ endpoint
