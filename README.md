<div align="center">
  <img height="50" src="https://www.nagarro.com/hubfs/NagarroWebsiteRedesign-Aug2020/Assets/Images/Nagarro%20green%20logo%20with%20white%20title.svg">
  <h1>JavaScript Interview Questions</h1>
  <small>Interview coding questions asked in Nagarro merged into one repository. A repo to preparing technical Interview for a Front-end Engineer position.  </small>
  
</div>
  
---

<span>Join me on this journey of repositories each of Startup's technical round's questions answers on my github account.

Test how well you know JavaScript, refresh your knowledge a bit, or prepare for your coding interview! :rocket:

Happy Coding! :heart:
Feel free to reach out to me! 😊 <br />
<a href="https://www.twitter.com/rajanmagarrr">Twitter</a> | <a href="https://www.linkedin.com/in/rajanmagarrr">LinkedIn</a>

---

###### 1. He asked me to choose 2 favorite topic from javascript. Ater thinking, I picked `Arrow Function` & `Destructuring`. On that he asked me to write 2 example where Arrow Function make sense over `Regular Function` and vice versa.

#### Answer: 
1st example is `map` Array method.
```javascript
const arr = [1,2,3,4];
const double = arr.map(num => num * 2);
console.log(double) 
▶ [2,4,6,8]
```
We can achieve same with regular function too but we have to use `curly brackets {}` and `return` keyword because it is not implicit like in Arrow function which makes code cleaner.
```javascript
const arr = [1,2,3,4];
const double = arr.map(function(num) {
return num * 2
};
console.log(double) 
▶ [2,4,6,8]
```
2nd example is `addEventListener` event. Regular function in events will return the element on which it used.
```javascript
[Element].addEventListener("click", function() {
    console.log(this)
})
▶ Element
```
While Arrow function in events will point to global scope hence return window object for this.
```javascript
[Element].addEventListener("click", () => console.log(this))
▶ Window
```
---
###### 2. In `Destructuring` objects, print out any two property from a nested object.
```javascript
const user = {
  name: "Rajan",
  address: {
    street: "Punjab"
  }
}
```
#### Answer:
```javascript
const { name, address: { street } } = user;
console.log(name, street);
▶ Rajan Punjab
```
---

###### 3. This was a followup question the previous question. Let's the `user` object is coming from an API and for one case, this user object is null. This will breake the application, so how will you fix it?
```javascript
const user = null;
const { name, address: { street } } = user;
console.log(name, street);
▶ Cannot read properties of null
```
#### Answer:
By using `spread` (...) operator.
```javascript
const { name, address } = {...user};
const { street } = {...address};
console.log(name, street);
▶ undefined undefined
```
--- 

###### 4. What is `callback hell`? Write an example of it.
#### Answer:
`Callback` hell is when you nest things inside of each other because they all depend on the previous callback to being called before it can then go ahead and run, when you need to run things in sequence, one after the other.

```javascript
const multiply = (num) => {
  multiplyBy2(num, (err, res) => {
    if(!err) {
      multiplyBy2(res, (err, res1) => {
        if(!err) {
          multiplyBy2(res1, (err, res2) => {
            console.log(res2);
          })
        } else {
          console.log("Error in Second call")
        }
      })
    } else {
      console.log("Error in first call ")
    }
  });
}
const multiplyBy2 = (num, fn) => {
  setTimeout(() => {
    fn(undefined, num * 2);
  }, 400)
}
multiply(10);
▶ 80
```
---

###### 5. Follow up question. How will you fix callback hell?
#### Answer:
Refactoring the previous code example by using Promise.
```javascript
const multiply = (num) => {
  multiplyBy2(num).then((data) => {
    multiplyBy2(data).then((data) => {
      multiplyBy2(data).then((data) => console.log(data))
    }).catch(err => console.log(err))
  }).catch(err => console.log(err))
}
const multiplyBy2 = (num) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(num * 2);
    }, 400)
  })
}
multiply(10);
▶ 80
```
---

###### 6. Output based question. What will be the output of below code and why?
 ```javascript
const object = {
  message: "Hello, World!",
  logMessage() {
    console.log(this.message);
  }
};
setTimeout(object.logMessage, 1000);
```
- A: `undefined`
- B: `null`
- C: `Hello, World!`
- D: `ReferenceError`
#### Answer:
<details><summary>I added the answer in the **collapsed sections** below, simply click on it to expand it.</summary>
<b>A</b> i.e. undefined
<p>Reason: setTimeout is taking <code>object.logMessage</code> method as regular function where this point to global scope i.e. <code>window</code> object.</p>
</details>
---

###### 7. Follow up question. How will you fix previous code?
```javascript
const object = {
  message: "Hello, World!",
  logMessage() {
    console.log(this.message);
  }
};
setTimeout(object.logMessage, 1000);
```
#### Answer:
By simply adding `Arrow Function` (=>) inside setTimeout, we convert reular funtion to arrow function.
```javascript
const object = {
  message: "Hello, World!",
  logMessage() {
    console.log(this.message);
  }
};
setTimeout(() => object.logMessage(), 1000);
```
