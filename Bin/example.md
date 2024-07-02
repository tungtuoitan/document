# code version 1

- việc load UI khá nặng
- khi typing liên tục --> update liên tục --> load UI liên tục --> bị lag toàn app
- khi dùng Suspense, nó khắc chế được việc load UI liên tục ?

In the example above,

<!-- there is no indication that the result list for the latest query is still loading.  -->

> > không có dấu hiệu của việc đang load last UI

<!-- This can be confusing to the user if the new results take a while to load. -->

điều này có thể làm user bối rối khi thời gian load dài
To make it more obvious to the user that the result list does not match the latest query, you can add a visual indication when the stale result list is displayed:

deferredValue update 5 lần
deferredValue update mỗi khi text update
