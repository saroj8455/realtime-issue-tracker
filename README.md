# realtime-issue-tracker and output-based questions and answer
A real-time issue was faced while  developing the app and with the solution.  

# template 

```md
## Link

[Markdown Live Preview](https://markdownlivepreview.com/).

## Blockquotes

> Markdown is a lightweight

## Blocks of code

```
let message = 'Hello world';
alert(message);
```
## Highlight code `highlight code`

### Ordered

1. Item 1
2. Item 2

## Lists

- [ ] What is Angular and why is it used?
```

## ``[WEB-001]`` : `$event.target.value` not resolved in Angular template 

`Object possible null`
```html
<label for="select"></label><select name="" id="select" (change)="onChange($event.target.value)">
    <option value="">Select combo</option>
    <option value="Value1">Text1</option>
    <option value="Value2">Text2</option>
    <option value="Value3">Text3</option>
</select>
```

#### Solution

```html
<select (change)="onChange($any($event.target).value)">
```

## Clamp Snippet for width and font size 

```css

.sidebar {
  /* 10rem min , 30vw perfer, 20rem max */
  width: clamp(10rem, 30vw, 20rem);
}

.sidebar .sidebar-header-text {
  /* responsive font size */
  font-size: clamp(1.5rem, 4.5vw, 2.5rem);
}

```

## React API call in useEffect quick snippets.

```jsx

  const [data, setData] = useState(null);
  const [user, setUser] = useState({});
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    const fetchData = async () => {
      setLoading(true);
      try {
        const response = await fetch(
          'https://jsonplaceholder.typicode.com/posts/-1'
        );
        if (!response.ok) {
          setError("Something went wrongs");
          return;
        }
        const jsonData = await response.json();
        setData(jsonData);
      } catch (error) {
        setError(error);
        
      } finally {
        setLoading(false);
      }
    };
    fetchData();
  }, []);
```

## Handel API call with loading, error, and data in react.

`Reactjs API call`, `quick snippets for API call`

```jsx
// Filename : App.jsx
import { useEffect, useState } from 'react';
import { useFetchData } from './hooks/useFetchData';
import { USERAPI } from './common/api';

function App() {
  const { loading, error, data: user } = useFetchData(USERAPI);
  const [users, setUsers] = useState({});

  useEffect(() => {
    console.log('useEffect run');
  }, []);

  return (
    <>
      <div className='flex flex-col gap-2 text-white min-h-screen bg-blue-600 justify-center items-center text-center'>
        {loading && <div className='text-4xl'>Loading...Please wait!.</div>}
        {error && <div className='text-4xl'>Error: {error}</div>}
        {user && <p className='text-4xl'>{user.title}</p>}
      </div>
    </>
  );
}

export default App;
```



















