# Question 1

The below code errors when you run it.

Make it run without errors but you cannot change the location of the `let` statement, that has to stay at the end.

```js
let i = 0;
function doAsyncTask(cb) {
  setImmediate(_ => {
    console.log("calling callback");
    cb();
    i++;
    console.log("i has been increased now: " + i);
  });
  console.log("should display before callback");
}
console.log("waiting for i to increment...Curent vallue of i is still " + i);

doAsyncTask(_ => console.log(message));

let message = "Callback Called";
```

# Question 2

The below code swallows the error and doesn't pass it up the chain, make it pass the error up the stack using the next callback.

```js
const fs = require("fs");

function readFileThenDo(next) {
  fs.readFile("./blah.nofile", (err, data) => {
    next(data);
  });
}

readFileThenDo(data => {
  console.log(data);
});
```

# Question 3

Instead of passing it up the stack throw it instead and try to catch it later on.

```js
const fs = require("fs");

function readFileThenDo(next) {
  fs.readFile("./blah.nofile", (err, data) => {
    if (err) throw err;
    next(data);
  });
}
// Hint use try..catch
readFileThenDo(data => {
  console.log(data);
});
```
