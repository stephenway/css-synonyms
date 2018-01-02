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

const foo = styled.div`
  font: 100% ${fontStack};
  color: ${primaryColor};
`;
```

### Import another file

Sass
```sass
@import 'reset';
```

Javascript
```js
import { reset } from './reset';
```
*MDN Reference: [import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)*


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
