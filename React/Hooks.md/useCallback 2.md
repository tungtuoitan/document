# useCallback()

- chứ năng: cache 1 [đối tượng function] giữa các lần re-render

## lưu ý khi dùng

- không được dùng trong loop/condition

- react sẽ chỉ throw away cached function khi:
  ta sửa code trong development enviroment
  khi component bị suspend trong quá trình initial mount (trong development + production enviroment)

## khi nào nên dùng useCallback()?

- truyền function vào memo component
- memozaition function dùng làm dependency cho 1 hook

## syntax

<!-- https://react.dev/reference/react/useCallback#parameters -->

## quan hệ giữa useCallback() và useMemo()

- useCallback là 1 hàm biến tấu của useMemo

function useCallback(fn, dependencies) {
return useMemo(() => fn, dependencies);}

## tại sao k dùng useCallback() ở mọi nơi ?

- k hiệu quả, k tối ưu được gì
- vỡ RAM, vì cái gì cũng cache hết
- code khó đọc

## usecase phổ biến và best practice

### dùng memozaition callback để update state

- best practice:
  function TodoList() {
  const [todos, setTodos] = useState([]);

  const handleAddTodo = **useCallback**((text) => {
  const newTodo = { id: nextId++, text };
  **setTodos(todos => [...todos, newTodo]);**
  }, **[]**);
  ...}

### dùng memoize callback làm dependency cho useEffect

- function ChatRoom({ roomId }) {
  const [message, setMessage] = useState('');

const createOptions = **useCallback**(() => {
return {
serverUrl: 'https://localhost:1234',
roomId: roomId
};
}, [roomId]); // ✅ Only changes when roomId changes

useEffect(() => {
const options = createOptions();
const connection = createConnection();
connection.connect();
return () => connection.disconnect();
}, **[createOptions]**); // ✅ Only changes when createOptions changes
...
}

### dùng useCallback để bọc các return function trong custom Hook

function useRouter() {
const { dispatch } = useContext(RouterStateContext);

const navigate = **useCallback**((url) => {
dispatch({ type: 'navigate', url });
}, [dispatch]);

const goBack = **useCallback**(() => {
dispatch({ type: 'back' });
}, [dispatch]);

return {
navigate,
goBack,
};
}

### dùng useCallback trong list

- VÍ DỤ CODE SAI:

function ReportList({ items }) {
return (

<article>
{items.map(item => {
// 🔴 You can't call useCallback in a loop like this:
const handleClick = useCallback(() => {
sendReport(item)
}, [item]);

        return (
          <figure key={item.id}>
            <Chart onClick={handleClick} />
          </figure>
        );
      })}
    </article>

);
}

- CODE ĐÚNG

function ReportList({ items }) {
return (

<article>
{items.map(item =>
<Report key={item.id} item={item} />
)}
</article>
);
}

function Report({ item }) {
// ✅ Call useCallback at the top level:
const handleClick = useCallback(() => {
sendReport(item)
}, [item]);

return (

<figure>
<Chart onClick={handleClick} />
</figure>
);
}
