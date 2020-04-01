# React Hooks

### Conditions

* Should be used only with **functional components**
* Hooks cannot be nested (no nested hooks)
*  should be imported from **react**

#### useState()

* This is replacement for **state** object which will be found in Class components

##### Syntax

```react
import React, { useState } from 'react';

function expensiveInitialState() {
  return 100;
}

const App = () => {
  const [count, setCount] = useState(10);
  const [anotherCount, setAnotherCount] = useState(() =>
    expensiveInitialState()
  );
  return (
    <div>
      {count}, {anotherCount}
      <br />
      <button onClick={() => setCount(count + 1)}>ADD</button>
    </div>
  );
};

export default App;
```

* When useState is used with a callback function, then state creation is expensive. So those expensive state creations with useState will be used along with **callbacks**. And when this done, the state will be **initialized** once not all the time the component renders

##### setState with callbacks

```react
import React, { useState } from 'react';

function expensiveInitialState() {
  return 100;
}

const App = () => {
  const [count, setCount] = useState(10);
  const [anotherCount, setAnotherCount] = useState(() =>
    expensiveInitialState()
  );
  return (
    <div>
      {count}, {anotherCount}
      <br />
      <button onClick={() => setCount(count + 1)}>ADD</button>
      <button onClick={() => setAnotherCount(currentCount => currentCount - 1)}>
        SUBTRACT
      </button>
    </div>
  );
};

export default App;
```

* This will avoid race conditions

##### useState with Objects

```react
import React, { useState } from 'react';

function expensiveInitialState() {
  return 100;
}

const App = () => {
  const [count, setCount] = useState(10);
  const [anotherCount, setAnotherCount] = useState(() =>
    expensiveInitialState()
  );
  const [{ objCount1, objCount2 }, setObjCounts] = useState({
    objCount1: 10,
    objCount2: 20
  });
  return (
    <div>
      {count}, {anotherCount}
      <br />
      <button onClick={() => setCount(count + 1)}>ADD</button>
      <button onClick={() => setAnotherCount(currentCount => currentCount - 1)}>
        SUBTRACT
      </button>
      <br />
      <p>Obj Count1: {objCount1} </p>
      <p>Obj Count2: {objCount2}</p>
      <button
        onClick={() =>
          setObjCounts(currentState => ({
            ...currentState,
            objCount1: currentState.objCount1 + 1
          }))
        }
      >
        + obj Count1
      </button>
      <button
        onClick={() =>
          setObjCounts(currentState => ({
            ...currentState,
            objCount2: currentState.objCount2 + 1
          }))
        }
      >
        + obj Count2
      </button>
    </div>
  );
};

export default App;
```

**changing two states at the same time**

```react
import React, { useState } from 'react';

function expensiveInitialState() {
  return 100;
}

const App = () => {
  const [count, setCount] = useState(10);
  const [anotherCount, setAnotherCount] = useState(() =>
    expensiveInitialState()
  );
  const [{ objCount1, objCount2 }, setObjCounts] = useState({
    objCount1: 10,
    objCount2: 20
  });
  return (
    <div>
      {count}, {anotherCount}
      <br />
      <button onClick={() => setCount(count + 1)}>ADD</button>
      <button onClick={() => setAnotherCount(currentCount => currentCount - 1)}>
        SUBTRACT
      </button>
      <br />
      <p>Obj Count1: {objCount1} </p>
      <p>Obj Count2: {objCount2}</p>
      <button
        onClick={() =>
          setObjCounts(currentState => ({
            ...currentState,
            objCount1: currentState.objCount1 + 1
          }))
        }
      >
        + obj Count1
      </button>
      <button
        onClick={() =>
          setObjCounts(currentState => ({
            ...currentState,
            objCount2: currentState.objCount2 + 1
          }))
        }
      >
        + obj Count2
      </button>
      <button
        onClick={() => {
          setCount(c => c + 1);
          setAnotherCount(c => c + 1);
        }}
      >
        Change All
      </button>
    </div>
  );
};

export default App;
```

#### useEffect()

**useEffect** will be called always whenever the component **renders**. This will also be called for all setStates.

```react
import React, { useState, useEffect } from 'react';

function App() {
  const [email, setEmail] = useState('');

  useEffect(() => {
    console.log('render');
  });

  return (
    <div>
      <input
        type="email"
        name="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
      />
    </div>
  );
}

export default App;
```

**To Prevent rendering always and to allow render(watch) only particular state**

#### Syntax

```react
import React, { useState, useEffect } from 'react';

function App() {
  const [email, setEmail] = useState('');

  useEffect(() => {
    console.log('render');
  }, [DEPENDENCY-ARRAY]);

  return (
    <div>
      {email}
    </div>
  );
}

export default App;
```

```react
import React, { useState, useEffect } from 'react';

function App() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  useEffect(() => {
    console.log('render');
  }, [password]);

  return (
    <div>
      <input
        type='email'
        name='email'
        value={email}
        onChange={e => setEmail(e.target.value)} />
      <input
        type="password"
        name="password"
        value={password}
        onChange={e => setPassword(e.target.value)} />
    </div>
  );
}

export default App;
```

> THIS ALLOWS SHALLOW CHECKING

**useEffect**

```react
import React, { useState, useEffect } from 'react';

function App() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  // This will render always
  useEffect(() => {
    console.log('render');
  });

  return (
    <div>
      <input
        type="email"
        name="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
      />
      <input
        type="password"
        name="password"
        value={password}
        onChange={e => setPassword(e.target.value)}
      />
    </div>
  );
}

export default App;
```

**componentDidMount with useEffect**

```react
import React, { useState, useEffect } from 'react';

function App() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  // componentDidMount
  useEffect(() => {
    console.log('render');
  }, []);

  return (
    <div>
      <input
        type="email"
        name="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
      />
      <input
        type="password"
        name="password"
        value={password}
        onChange={e => setPassword(e.target.value)}
      />
    </div>
  );
}

export default App;
```

**componentWillUnmount**

```react
import React, { useEffect } from 'react';

// componentDidMount
const Hello = () => {
  useEffect(() => {
    console.log('mounted');
    // componentWillUnmount
    return () => {
      console.log('unmounted');
    };
  }, []);

  return <div>Hello</div>;
};

export default Hello;
```

**Multiple useEffects**

```react
import React, { useState, useEffect } from 'react';

function App() {
  const [email, setEmail] = useState('');
  useEffect(() => {
    console.log('mount1');
  });
  useEffect(() => {
    console.log('mount2');
  });
  return (
    <div>
      <input
        value={email}
        type="email"
        onChange={e => setEmail(e.target.value)}
      />
    </div>
  );
}
export default App;
```

**Custom useEffect for API Fetch**

```react
// App.js
import React, { useState } from 'react';

import { useFetch } from './useFetch';

function App() {
  const [url, setUrl] = useState(1);
  const { data, loading } = useFetch(`http://numbersapi.com/${url}/trivia`);
  const getData = e => {
    if (e.target.value) {
      setUrl(e.target.value);
    }
  };
  return (
    <div>
      <input
        type="email"
        value={url}
        onChange={e => getData(e)}
        style={{ display: 'block' }}
      />
      {loading ? <div>Data is Loading</div> : data}
    </div>
  );
}

export default App;
```

```react
// useFetch
import { useEffect, useState } from 'react';

export const useFetch = url => {
  const [state, setState] = useState({ data: null, loading: false });
  useEffect(() => {
    setState(state => ({
        data: state.data,
        loading: true
    }));
    fetch(url)
      .then(x => x.text())
      .then(y =>
        setState({
          data: y,
          loading: false
        })
      );
  }, [url]);
  return state;
};

```

#### useRef()

* Alternative of `React.createRef()` in functional based components

```react
import React, { useRef, useEffect } from 'react'

const cockpit = (props) => {
  const toggleRef = useRef(null);
  
  useEffect(() => {
    toggleRef.current.click();
  }, []);
  
  return (
   <button ref={toggleRef} >click</button>
  );
}
```

####  useContext()

* This is an alternative for **static contextType** in class based components

```react
import React from 'react';

import AuthContext from './context/context';

const Login = (props) => {
  const authContext = useContext(AuthContext);
  console.log(authContext);
  return (
  	<p>{authContext.authenticated}</p>
    <button onClick={authContext.login}>click</button>
  );
}
```



















