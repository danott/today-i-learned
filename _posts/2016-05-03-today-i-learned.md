`import` statements can be picky When using ES2015.
With the variety of Babel plugins and configurations it's easy to have some technically invalid syntax that compiles just fine in that configuration.

```javascript
// family.js
export default {
  george: "Grandpa",
  michael: "Dad",
  maeby: "Cousin",
}

// uses_family.js
import { maeby } from "./family.js"
```

I don't know what plugin I was relying on but previously this import statement worked.
It turns out that destructuring off a default export is not actually a thing.

Option 1:

```javascript
// family.js
export const george = "Grandpa"
export const michael = "Dad"
export const maeby = "Cousin"
export default { george, michael, maeby }

// uses_family.js
import { maeby } from "./family.js"
```

Option 2:

```javascript
// family.js
export default {
  george: "Grandpa",
  michael: "Dad",
  maeby: "Cousin",
}

// uses_family.js
import Family from "./family.js"
const { maeby } = Family
```
