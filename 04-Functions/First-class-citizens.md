# What does it means thaht function are first class citizen in JS? 

 - We can assign it to variable 

 ```js
 const result = function () {}
 ```

 - We can pass function as an argument of other function 

 ```js
 function a (fn) {
    fn()
 }
 a(function(){console.log('Hi there')})
 ```