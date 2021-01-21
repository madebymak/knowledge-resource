# React

## Function Declarations & Arrow Functions
- react function component returns JSX
- primary benefit of arrow functions is their succinctness (clear, precise expression)
```
// Function declaration syntax
function MyComponent(props) {
  return <div>{props.content}</div>;
}

// Arrow function syntax
const MyComponent = (props) => {
  return <div>{props.content}</div>;
}

// Arrow function syntax (shorthand)
const MyComponent = props => <div>{props.content}</div>;
```
<br>

## useEffect()
- hook that manages side-effects in functional React components
- alternative to `setState()` in class components
- runs after every render unless a second argument is provided

```
// state change example
function ThreeCounts() {
  const [count1, setCount1] = useState(0);
  const [count2, setCount2] = useState(0);
  const [count3, setCount3] = useState(0);

  useEffect(() => {
    console.log("count2 changed!");
  }, [count2]); // provide a second argument if you don't want it often

  return (
    <div>
      {count1} {count2} {count3}
      <br />
      <button onClick={() => setCount1(count1 + 1)}>Increment count1</button>
      <button onClick={() => setCount2(count2 + 1)}>Increment count2</button>
      <button onClick={() => setCount3(count3 + 1)}>Increment count3</button>
    </div>
  );
}
```
<br>

