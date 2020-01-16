---
layout: page
title: "Difference between var and let in Javascript"
subheadline: "var and let in javascript"
teaser: Showing the difference between var and let in javascript variable declaration. Removing all confusions about var and let method of javascript. 
sidebar: right
comments: true
header: no
image:
    title: js-var-vs-let.jpg
    thumb: js-var-vs-let.jpg
    homepage: js-var-vs-let.jpg
    caption: "javascript (let vs var)"
categories: 
    - javascript
---

Have you ever wondered what's the difference between `let` and `var` in Javascript? I know, everyone faces some problems with them when they start learning Javascript for the first time. Are they the same? If so, why did programmers impliment them differently? Let's find it out. 

As we all know, everything has a unique purpose. `let` and `var` are not the same. You can use any of them to declare variables, but there are some internal differences between them. I hope you will be able to understand them after reading the article. 

I am assuming that you know some basic javascripts. Let's start with some codes. Then I'll explain that. Open your browser and press `ctrl+shift+i` to open the `inspect element` tab. Then write the following code to see what's the result.

```js
var x = 10;
console.log(x);
```
The console will print 10. That's fine. now run the following code. 
```js
let p = 10;
console.log(p);
```
It prints 10 too. So it doesn't seem there is a difference between them. Now we will discuss about `let` and `var` differently and you will understand everything. 

# let

In a nutshell, `let` only works inside a block. If you declare a variable with `let` inside a javascript block, it won't work outside that. First we need to work with some html. Copy the following html code and paste it into a file. iet's assume the file name is `index.html`. The name can be anything though.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Document</title>
</head>
<body>
    <h1>Testing some Js stuff</h1>
    <script>
        // here we will work with some javascript codes to understand.
    </script>
</body>
</html>
```
It's a simple code. Here we will just examine our javascript codes. It'll be easy now. Paste the following codes inside the `<script>` tag and go to the console to see what happens. 
```js
let x = 12;
if(x == 12){
    console.log('hello world');
}
console.log(x);
```
It will print `Hello world` in the first line and 12 in the second line, as expected. So what happens here, we declared x using `let` and assigned 12 inside the variable. Since `x == 12` is true, it'll go to the conditional block and print `Hello World` and then print 12 in the second line. But what if you replace the code with the following one? 
```js
let p = 12;
if(p == 12){
    let x = 13;
    console.log('hello world');
}
console.log(x);
```
Now, as before, the firs line of the output will contain `Hello world` but then we will get some error, `Uncaught ReferenceError: x is not defined` which means the compiler is tellig us that, x is not declared. But have a look at the code, we did declare x with `let` inside the conditional block! As we declared x inside the if block, x is not visible outside that. so if you move the console.log(x) line inside the if block, the compiler will print 13 because x is declared there. Let's check. 
```js
let p = 12;
if(p == 12){
    let x = 13;
    console.log('hello world');
    console.log(x);
}
```
Now run this ans it'll work fine. So the first thing we learned is, if we use `let` inside a block, it'll not be visible outside the block. The block can be a conditional logic, loop, function etc. the following loop is also a block. 
```js
let i = 0;
for(i = 0;i <= 10;i++){
    let x = 12;
    console.log(x);
    // this x is only visible inside this particular loop.
}
// x is not visible here.
```

Now we will work with  `var`

# var

var declares a variable globally. So it doesn't matter where you declare the variable using var, you'll be able to use it. Run the following code for better understanding.
```js
var p = 12;
if(p == 12){
    var x = 133;
    console.log('hello world');
}
console.log(x);
```

Here, we declared x inside the conditional block, but still it works. Now let's see an absolute magic.
```js
x = 12;
console.log(x);
var x;
```

Here we declared x after consoling the value. But still it gives us a correct answer. It's because whenever we declare something with var, it'll go all the way up of the code. So, when we execute the last code, the code will be replaced with this: 
```js
var x;
x = 12;
console.log(x);
```
That's why we don't get any error messages. Now let's see an another exaple, this example is very important. 
```js
console.log(x);
var x = 12;
```

Can you tell me the output before running the code? If your ans is 12, you're wrong! Actually the code will be replaced with the following code:
```js
var x;
console.log(x);
x = 12;
```
This means, you declared x but didn't specify the value. That's why the value will be `undefined`. So we cleared something, let declares a variable inside a block and var declares a variable globally. It should be clear now. Peace.