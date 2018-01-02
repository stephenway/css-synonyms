# styled-components

### Variables

Sass
```sass
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

.foo {
  font: 100% $font-stack;
  color: $primary-color;
}
```

Javascript
```js
const fontStack = 'Helvetica, sans-serif';
const primaryColor = '#333';

const Foo = styled.div`
  font: 100% ${fontStack};
  color: ${primaryColor};
`;
```

### Nesting

Sass
```sass
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  
  li { display: inline-block; }
  
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

Javascript
```js
const Nav = styled.nav`
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  
  li { display: inline-block; }
  
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
`;
```

### Import another file

Sass
```sass
// Import _reset.scss file
@import 'reset';
```

Javascript
```js
// Import reset.js file
import { reset } from './reset';
```
*MDN Reference: [import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)*

### Mixins

Sass
```sass
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

Javascript

* We are exporting this function because a Sass mixin is already accessible from outside the file it's in.
* Basic CSS rules like `border-radius` are written in cammel case (`borderRadius`) in Javascript objects.
```js
export function borderRadius(radius) {
  '-webkit-border-radius': radius,
     '-moz-border-radius': radius,
      '-ms-border-radius': radius,
             borderRadius: radius,
}
```

### Printing an error

Sass
```sass
@error "Sorry, but `#{$variable}` is not a valid value for $variable.";
```

Javascript
```js
throw new Error(`Sorry, but ${variable} is not a valid value for variable.`);
```
*MDN Reference: [Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)*
