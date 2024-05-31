# How to Change the Theme System in Tailwind CSS

Tailwind CSS is a highly customizable CSS framework that allows you to easily change and extend the default theme to match your design needs. This guide will walk you through the steps to modify the theme configuration in Tailwind CSS.

`index.css`

````javascript
@tailwind base;
@tailwind components;
@tailwind utilities;

//define colors in rgb way if we use hex color we miss the alpha channel
//reason for remove rgb keyword, these color will again access ```tailwind.config.js``` then we define the rgba channel

@layer base {
  :root {
    --color-text-base: 255, 255, 255;
    --color-text-muted: 199, 210, 254;
    --color-text-inverted: 79, 70, 229;

    --color-fill: 67, 56, 202;
    --color-button-accent: 255, 255, 255;
    --color-button-accent-hover: 238, 242, 255;
    --color-button-muted: 99, 102, 241;
  }

  .theme-swiss {
    --color-text-base: 255, 255, 255;
    --color-text-muted: 254, 202, 202;
    --color-text-inverted: 220, 47, 47;

    --color-fill: 220, 47, 47;
    --color-button-accent: 255, 255, 255;
    --color-button-accent-hover: 254, 242, 242;
    --color-button-muted: 239, 68, 68;
  }
}


````

`tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */

function withOpactity(variableName) {
  return ({ opacityValue }) => {
    if (opacityValue !== undefined) {
      return `rgba(var(${variableName}), ${opacityValue})`;
    }
    return `rgb(var(${variableName}))`;
  };
}
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      textColor: {
        skin: {
          base: "var(--color-text-base)",
          muted: "var(--color-text-muted)",
          inverted: "var(--color-text-inverted)",
        },
      },
      backgroundColor: {
        skin: {
          fill: withOpactity("--color-fill"),
          "button-accent": withOpactity("--color-button-accent"),
          "button-accent-hover": withOpactity("--color-button-accent-hover"),
          "button-muted": withOpactity("--color-button-muted"),
        },
      },
      gradientColorStops: {
        skin: {
          hue: withOpactity("--color-fill"),
        },
      },
    },
  },
  plugins: [],
};
```

## before

```javascript
const App = () => {
  return (
    <div className="space-y-6 m-6">
      <div className="relative max-w-4xl mx-auto bg-blue-700 rounded-2xl overflow-hidden">
        <img
          className="absolute inset-0 h-full w-full object-cover opacity-30"
          src="https://pixabay.com/illustrations/hand-robot-ai-hold-future-space-7014643/"
          alt="People working on laptops"
        />
        <div className="absolute inset-0 bg-gradient-to-br from-blue-700 via-blue-700 to-transparent opacity-90"></div>
        <div className="relative max-w-2xl mx-auto text-center py-16 px-4 sm:py-20 sm:px-6 lg:px-8">
          <h2 className="text-3xl font-extrabold text-white sm:text-4xl">
            <span className="block">Looking for next generation AI ?</span>
            <span className="block">We provide you best in the world.</span>
          </h2>
          <p className="mt-4 text-lg leading-6 text-gray-100">
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vero
            nesciunt perferendis corporis tempore eum.
          </p>

          <div className="mt-10 max-w-sm mx-auto sm:max-w-none sm:flex sm:justify-center">
            <div className="space-y-4 sm:space-y-0 sm:mx-auto sm:inline-grid sm:grid-cols-2 sm:gap-5">
              <a
                href="#"
                className="border border-transparent px-4 py-3 rounded-md capitalize font-semibold text-base flex items-center justify-center shadow-md sm:px-8 bg-white bg-opacity-90 hover:bg-opacity-100 text-blue-500"
              >
                Get started
              </a>
              <a
                href="#"
                className="border border-transparent px-4 py-3 rounded-md capitalize font-semibold text-base flex items-center justify-center shadow-md sm:px-8 bg-blue-600 bg-opacity-60 text-white hover:bg-opacity-70"
              >
                live demo
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default App;
```

## after

```javascript
const App = () => {
  return (
    <div className="space-y-6 m-6">
      <div className="relative max-w-4xl mx-auto bg-skin-fill rounded-2xl overflow-hidden">
        <img
          className="absolute inset-0 h-full w-full object-cover opacity-30"
          src="https://images.unsplash.com/photo-1613217784112-e0e197be6a0b?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1600&q=80&sat=-100"
          alt="People working on laptops"
        />
        <div className="absolute inset-0 bg-gradient-to-br from-skin-hue via-skin-from-skin-hue to-transparent opacity-90"></div>
        <div className="relative max-w-2xl mx-auto text-center py-16 px-4 sm:py-20 sm:px-6 lg:px-8">
          <h2 className="text-3xl font-extrabold text-skin-base sm:text-4xl">
            <span className="block">Looking for next generation AI ?</span>
            <span className="block">We provide you best in the world.</span>
          </h2>
          <p className="mt-4 text-lg leading-6 text-skin-muted">
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vero
            nesciunt perferendis corporis tempore eum.
          </p>

          <div className="mt-10 max-w-sm mx-auto sm:max-w-none sm:flex sm:justify-center">
            <div className="space-y-4 sm:space-y-0 sm:mx-auto sm:inline-grid sm:grid-cols-2 sm:gap-5">
              <a
                href="#"
                className="border border-transparent px-4 py-3 rounded-md capitalize font-semibold text-base flex items-center justify-center shadow-md sm:px-8 bg-skin-button-accent bg-opacity-90 hover:bg-opacity-100 text-skin-inverted"
              >
                Get started
              </a>
              <a
                href="#"
                className="border border-transparent px-4 py-3 rounded-md capitalize font-semibold text-base flex items-center justify-center shadow-md sm:px-8 bg-skin-fill bg-opacity-60 text-skin-base hover:bg-opacity-70"
              >
                live demo
              </a>
            </div>
          </div>
        </div>
      </div>

      <div className="relative max-w-4xl mx-auto bg-skin-fill rounded-2xl overflow-hidden theme-swiss">
        <img
          className="absolute inset-0 h-full w-full object-cover opacity-30"
          src="https://images.unsplash.com/photo-1613217784112-e0e197be6a0b?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1600&q=80&sat=-100"
          alt="People working on laptops"
        />
        <div className="absolute inset-0 bg-gradient-to-br from-skin-hue via-skin-from-skin-hue to-transparent opacity-90"></div>
        <div className="relative max-w-2xl mx-auto text-center py-16 px-4 sm:py-20 sm:px-6 lg:px-8">
          <h2 className="text-3xl font-extrabold text-skin-base sm:text-4xl">
            <span className="block">Looking for next generation AI ?</span>
            <span className="block">We provide you best in the world.</span>
          </h2>
          <p className="mt-4 text-lg leading-6 text-skin-muted">
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vero
            nesciunt perferendis corporis tempore eum.
          </p>

          <div className="mt-10 max-w-sm mx-auto sm:max-w-none sm:flex sm:justify-center">
            <div className="space-y-4 sm:space-y-0 sm:mx-auto sm:inline-grid sm:grid-cols-2 sm:gap-5">
              <a
                href="#"
                className="border border-transparent px-4 py-3 rounded-md capitalize font-semibold text-base flex items-center justify-center shadow-md sm:px-8 bg-skin-button-accent bg-opacity-90 hover:bg-opacity-100 text-skin-inverted"
              >
                Get started
              </a>
              <a
                href="#"
                className="border border-transparent px-4 py-3 rounded-md capitalize font-semibold text-base flex items-center justify-center shadow-md sm:px-8 bg-skin-fill bg-opacity-60 text-skin-base hover:bg-opacity-70"
              >
                live demo
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default App;
```

- now we can use defferent theme only changing theme variable
