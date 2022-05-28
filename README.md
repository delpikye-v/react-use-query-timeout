<div align="center">
    <h1>react-use-query-timeout</h1>
    <br />
    <a href="https://codesandbox.io/s/uu5etr">LIVE EXAMPLE</a>
</div>

---

#### Description

+ Simple use query graphql (react-hook) with timeout.
+ Default timeout 10m
+ From @apollo/client :v

---

#### Usage
```js
npm install react-use-query-timeout
```

Import the module in the place you want to use:
```js

import { useQueryTimeout } from 'react-use-query-timeout'
```


#### Snippet

##### `simple`

```js
    const [request, setRequest] = useState<number | boolean | string>(0);
     // start request in { true | number !== 0 | string !== empty }

    const { data: queryData, loading, isRequestTimeout, error } = useQueryTimeout(QUERY, {
        variables: {
          start: xxx,
          end: xxx,
          ...
        },
        timeout: 60 * 1000, // 60s
        flagNewQuery: request,
        clearFlagNewQuery: setRequest
    });

    useEffect(() => {
        if (!loading) {
            console.log(queryData, loading, isRequestTimeout, error)
            debugger
        }
    }, [loading])


    // => change it => auto make new query
    <Button onClick={() => setRequest(+ new Date())}>Abcd</Button>
```

<br />

##### `simple`

```js

    const { fetchQuery } = useQueryTimeout(QUERY, {
        variables: {
          start: xxx,
          end: xxx,
          ...
        },
        timeout: 60 * 1000, // 60s
    });

    const handlerAbc = () => {
        fetchQuery().then((rresult) => {
            console.log(rresult) // rresult.data | error | { isRequestTimeout }
            debugger
        })
    }


    <Button onClick={() => handlerAbc()}>Abcd</Button>
```
<br />

---

#### props


<br />

#### RUN

<a href="https://codesandbox.io/s/uu5etr">LIVE EXAMPLE</a>

```js
npm install
```
```js
npm run dev
npm run start
```

### License

MIT
