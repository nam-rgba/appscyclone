# 1. HTML
- Structure of website
## Common questions, tips and tricks
- 1. Metadata tag: 
=> Use to provide metadata of webpage like information, description, keywords, authors...
    + Charset: character encoding
    + Viewport: control layout of mobile browser
    + Description: keep decription of webpage, for search result

- 2. 2 types of a tag:
    It's 2 type of HTLM tag: Block and Inline, but usually can edit by CSS
- 3. Common tag:
    + p: paragraph
    + div: block
    + section: define a section of webpage
    + hx: heading
    + b: bold
    + button: button
    ...
- 4. About DOM:
     The DOM provides a structured, object-oriented representation of the HTML document, which can be manipulated with JavaScript.


# 2. CSS
## 1. Position:
* Absolute: depent on parent
* Relative: usually use to parent
* Fixed: keep position in screen from init value
* Sticky: when element come to position, it will not change


## 2. Flex
* Display: define a flex container
* Direction: establish the main axis
* Grow: define an item to grown size if necessary
* Wrap: one line or more
* Justify content: alighment main axis
* Align item: alignment remain axsis
* Gap: control space between items

## 3. Display
* Block: can change width, height, appear base on content, children
* Inline: with auto full, height base on content
* None: not appear

## 4. Box model
    * Margin: outside the border, will not apply normal orther propertypes css
    * Border: Frame, boundairy of element
    * Padding: inside border,  apply normal orther propertypes css


# 3. BEM

Clean code for CSS, it contain:
 + Block: standalone element like header, container, button, input,...
 + Element: a part of a block eg.: menu_item, input_feild,...
 + Modifier: A modifier is a flag on a block or element. It defines the appearance, state, or behavior.

 # 4. SCCS

 + Variable: 
 ```
$primary-color: #007bff;
$font-stack: Helvetica, sans-serif;
```

+ Nesting:
```
nav {
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
    
    li {
      display: inline-block;
      margin-right: 10px;
      
      a {
        text-decoration: none;
        color: $primary-color;
        
        &:hover {
          color: darken($primary-color, 10%);
        }
      }
    }
  }
}

```

+ Import:
```
// _variables.scss
$primary-color: #007bff;
$font-stack: Helvetica, sans-serif;

// _base.scss
body {
  font-family: $font-stack;
  color: $primary-color;
}

// styles.scss
@import 'variables';
@import 'base';

```

+ Mixin:
```
@mixin button-styles($color) {
  padding: 10px 20px;
  border-radius: 5px;
  background-color: $color;
  color: #fff;
  text-decoration: none;
  display: inline-block;
  
  &:hover {
    background-color: darken($color, 10%);
  }
}

.button {
  @include button-styles($primary-color);
}

```

+ Extend/Inheritance:
```
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}

```

+ Operators:
```
.container {
  width: 100% - 20px;
  height: 100vh;
  padding: 10px;

  .box {
    width: (100% / 3) - 20px;
    margin: 10px;
    float: left;
  }
}

```

## Responsive 
With pure CSS, we use media query:
```
@media media-type and (media-feature-rule) {
  /* CSS rules go here */
}
```

The feature we tend to detect most often in order to create responsive designs (and that has widespread browser support) is viewport width, and we can apply CSS if the viewport is above or below a certain width — or an exact width — using the min-width, max-width, and width media features.

These features are used to create layouts that respond to different screen sizes. For example, to change the body text color to red if the viewport is exactly 600 pixels, you would use the following media query.

```
@media screen and (width: 600px) {
  body {
    color: red;
  }
}

```

# 5. Tailwind CSS
Install:
    ```
    npm install -D tailwindcss postcss autoprefixer
    npx tailwindcss init -p
    ```

Usage, config path, color scheme define:
    ``` 
    export default {
    content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
    ],
    theme: {
        colors:{
        transparent: 'transparent',
        current: 'currentColor',
        gray1: '#656e83',
        white:'#ffffff',
        warning1:'#fe7d8b',
        green_1: '#217d47',
        blue_1: '#1a91f0',
        green_2: '#e7f4ed',
        text_1:'#1e2532',
        bg_1: '#eff2f9',
        bg_2:'#e7e9f9',
        purple: '#343ecc',
        purple2:'#7a82f5',
        gray_text: '#828ba2'
        },
        extend: {
        transitionProperty:{
            border_width: 'border-width',
        }
        }
    },
    plugins: [],
    }
    ```

Custom value:

```
<div className='h[69px]'>
```
# 6. Javascript (ES6 default)
## 1. Declare key word
+ Let: Block scope
+ Var: Function scope
+ Const: Constants

## 2. Type
Number, String, Object, Null, Undefine

## 3. Template Literals
```
const firstName = "Nam";
const lastName = "Doan";

console.log("Hello " + firstName + " " + lastName);
console.log(`Hello ${firstName} ${lastName}`);
```

## 4. Arrow Function
```
let product = (x, y) => x * y;

result = product(5, 10);
```

## Destructering 
```
const hospital = {
    doctors: 23,
    patients: 44,
};

// use ES6 destructuring syntax
let { doctors, patients } = hospital;

```


## Export and Import
```
export default function greet(name) {
    console.log(`Hi ${name}!`);
};
```

```
import greet from './action.js';

greet("Sara");
```

## About async/await and promise
A promise may have one of three states:
+ Pending
+ Fullfilled
+ Rejected

A promise start with pending, that means the process is not completed. 
If the operation successfull, the state change to fulfilled.
And, if have any errors occurs, the process end in a rejected state.

```
const count = true;

let countValue = new Promise(function (resolve, reject) {
    if (count) {
        resolve("There is a count value.");
    } else {
        reject("There is no count value");
    }
});

console.log(countValue);
```


* Method
- all: Waits for all promises to be resolved or any one to be rejected
- any: Returns the promise value as soon as any one of the promises is fulfilled
- race: Wait until any of the promises is resolved or rejected
- reject: Returns a new Promise object that is rejected for the given reason
- resolve: Returns a new Promise object that is resolved with the given value
- catch: Appends the rejection handler callback
- then: Appends the resolved handler callback


A Javascript Promise is like having a box with a red and green light on it. One of the lights will light up, but you don't know when. If the light turns green(promise resolves), a cookie appears inside the box. If the light turns red(promise rejects or error), a note will appear in the box with a reason why the cookie didn't appear. You need to promise ahead of time what you will do right after the light turns green(maybe eat the cookie?) and what you will do if the light turns red(throw a tantrum?).

From ES7, we were provide Async/await to handle asynchronous
We use the async keyword with a function to represent that the function is an asynchronous function. The async function returns a promise.
The await keyword is used inside the async function to wait for the asynchronous operation.

```
// a promise
let promise = new Promise(function (resolve, reject) {
    setTimeout(function () {
    resolve('Promise resolved')}, 4000); 
});

// async function
async function asyncFunc() {

    // wait until the promise resolves 
    let result = await promise; 

    console.log(result);
    console.log('hello');
}

// calling the async function
asyncFunc();
```






