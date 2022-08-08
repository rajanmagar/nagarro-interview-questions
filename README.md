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
