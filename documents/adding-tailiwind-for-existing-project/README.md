# Add Tailwind CSS for existing project

we can add tailwind css for existing project even it was not write in tailwind.

`tailwind.config.js`

```javascript
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],

  corePlugins: {
    preflight: false,
  },
  prefix: "tw-",
  theme: {
    extend: {},
  },
  plugins: [],
};
```

```
corePlugins: {preflight: false,}

 use for disable all default css that provide taiwlind at the  begining
```

```
prefix: "tw-",

use for add prefix to tailwind utility class then it avoid naming collision with existing css

```
