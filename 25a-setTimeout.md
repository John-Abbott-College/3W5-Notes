# setTimeout

A useful function to run a function asynchronously after a given amount of time.

Note! It returns right away, just sets up the asynchronous operation to occur

- takes in two parameters:

  - The function to run after the specified time. The function takes no parameters.
  - The specified time in ms (1000ms = 1s).

  

  ```javascript
  function test(){ alert("Hi!")};
  
  //runs test after 2s, i.e, will alert Hi after 2s
  setTimeout( test, 2000 );
  
  //will log Bye to the console after 8s
  setTimeout( ()=>{console.log("Bye")}, 8000);
  
  ```

  

As the function given to `setTimeout` is run asynchronously after the elapsed time, it will be picked up by the main runner only when it is free. Therefore:



```javascript
console.log("A");
setTimeout( ()=>{console.log("B"), 0 );
console.log("C");
setTimeout( ()=>{console.log("D")}, 0);
console.log("E");
                 
//will log:
//A
//C
//E
//B
//D
```

