# Hoạt động của React

## Triggering

- update state/props...
- tạo ra queue render

## Rendering

- chạy component function để tạo JSX (đây là hoạt động đệ quy)
- so sánh với preJSX để tìm ra những chi tiết cần update

## Committing (tức React commit change to DOM)

(là giai đoạn áp dụng những chi tiết cần thay đổi vào DOM)

- update DOM

*RUN callback in useEffect synchronously khi việc show lastest UI là quan trọng (hiếm khi xảy ra)*

## paint screen (tức browser rendering)

**RUN callback in useEffect asynchronously (most of the time)**

# source

<!-- https://react.dev/learn/render-and-commit -->
<!-- https://jser.dev/2023-08-09-effects-run-paint/ -->
