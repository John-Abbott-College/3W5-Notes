# setTimeout

A useful function to run a function asynchronously after a given amount of time.

Note! It returns right away, just sets up the asynchronous operation to occur

- takes in two parameters:

  - The function to run after the specified time. The function takes no parameters.
  - The specified time in ms (1000ms = 1s).

  

  

  ```javascript
  function test(){ alert("Hi!")};
  
  //runs test after 2s
  setTimeout( test, 2000 );
  
  ```

  
