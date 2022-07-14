# req.query
- using ? in url.
- It's taken the query parameter after ? in URL and turn it into JSON.
- the following is req.query when URL is " http://localhost:3001/api/animals?name=Erica"
```js
{name: 'Erica}
```
- "?a=111&b=222&c=333" will become:
- req.query is:
```js
{
    a: "111",
    b: "222",
    c: "333"
}
```
- if you repeat the same query name with different values, it will become an array in the JSON.
- "?a=111&b=222&b=333" would become 
- req.query:
```js
{
    a: "111",
    b: ["222", "333"]
}
```

# req.params === the param object needs to be defined in the route path. 
- definiation "<route>/:<parameterName>" URL: "http://localhost:3001/api/animals/1"

## req.query is multifaceted, often combining multiple parameters, 
## whereas req.param is specific to a single property, often intended to retrieve a single record.