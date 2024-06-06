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




