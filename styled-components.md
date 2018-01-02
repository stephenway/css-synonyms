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

1. If you want to make a constant/variable made available to other files outside the current one, you need to prepend it with `export`.
2. When using 

```js
export const fontStack = 'Helvetica, sans-serif'; // 1
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

1. We are exporting this function because a Sass mixin is already accessible from outside the file it's in.
2. Basic CSS rules like `border-radius` are written in cammel case (`borderRadius`) in Javascript objects.
3. When passing values to method arguments, we give it a string when providing the unit (px, em, etc.)
4. Extend isn't a pattern that has been defined, not sure if it needs to be as that technique has been [proven not to be a best practice](https://www.sitepoint.com/avoid-sass-extend/).

```js
export function borderRadius(radius) { // 1
  '-webkit-border-radius': radius,
     '-moz-border-radius': radius,
      '-ms-border-radius': radius,
             borderRadius: radius, // 2
}

const Box = styled.div`
  ${borderRadius('10px')} // 3
`;
```

### Operators

Sass
```sass
.container { width: 100%; }

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```

Javascript
```js
const Container = styled.div`
  width: 100%;
`;

const Article = styled.article.attrs({
  role: 'main',
})`
  float: left;
  width: ${600 / 960 * 100}%;
`;

const Aside = styled.aside.attrs({
  role: 'complementary',
})`
  float: right;
  width: ${300 / 960 * 100}%;
`;
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
