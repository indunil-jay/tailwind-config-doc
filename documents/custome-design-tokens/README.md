# Create Custome design tokens By overriding existigs

- custome screen sizes
- colors
- box-shadow
- font-sizes
- font-family

`index.css`

```javascript
@tailwind base;
@tailwind components;
@tailwind utilities;

/*
in order to use custome font natively in design we need to do below things
src link for downloaded font directory */

@layer base {
  @font-face {
    font-family: "Inter";
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url("/fonts/Inter-Regular.ttf") format("truetype");
  }

  @font-face {
    font-family: "Inter";
    font-style: normal;
    font-weight: 500;
    font-display: swap;
    src: url("/fonts/Inter-Medium.ttf") format("truetype");
  }

  @font-face {
    font-family: "Inter";
    font-style: normal;
    font-weight: 600;
    font-display: swap;
    src: url("/fonts/Inter-SemiBold.ttf") format("truetype");
  }

  @font-face {
    font-family: "Satoshi";
    src: url("/fonts/satoshi.ttf") format("truetype");
    font-display: swap;
    font-weight: 900;
    font-style: normal;
  }
}


```

`tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */

export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
    screens: {
      tablet: "960px",
      desktop: "1248px",
    },
    colors: {
      white: "#ffffff",
      purple: "#3f3cbb",
      midnight: "#121063",
      metal: "#565584",
      "tahiti-blue": "#3ab7bf",
      "cool-white": "#ecebff",
      "light-rose": "#ff77e9",
      "copper-rust": "#78ddca",
    },

    boxShadow: {
      sm: "0px 2px 4px 0px rgba(11,10,55,0.15)",
      md: "0px 8px 20px 0px rgba(18,16,99,0.06)",
    },

    fontSize: {
      xs: ["14px", { lineHeight: "24px", letterSpacing: "-0.03em" }],
      sm: ["16px", { lineHeight: "28px", letterSpacing: "-0.03em" }],
      lg: ["18px", { lineHeight: "28px", letterSpacing: "-0.03em" }],
      xl: ["24px", { lineHeight: "36px", letterSpacing: "-0.03em" }],
      "2xl": ["36px", { lineHeight: "48px", letterSpacing: "-0.032em" }],
      "3xl": ["48px", { lineHeight: "56px", letterSpacing: "-0.032em" }],
      "4xl": ["56px", { lineHeight: "64px", letterSpacing: "-0.032em" }],
      "5xl": ["80px", { lineHeight: "80px", letterSpacing: "-0.032em" }],
    },

    fontFamily: {
      satoshi: "Satoshi, sans-serif",
      inter: "Inter, sans-serif",
    },
  },
  plugins: [],
};
```
