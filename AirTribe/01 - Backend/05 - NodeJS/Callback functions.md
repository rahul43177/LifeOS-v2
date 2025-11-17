### code 
```js 
const asyncFunction = (cb) => {
    setTimeout(() => {
        console.log("In between")
        cb();
    }, 1000)
}

const main = () => {
    console.log("Start");
    asyncFunction(() => {
        console.log("END");
    })
}


main()
```

- So here in the `main` function we are passing another function and that is a callback function 
- The output of this would be 
```plain text
Start
In between
END
```


