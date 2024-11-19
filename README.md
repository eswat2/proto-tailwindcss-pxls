# proto-tailwindcss-pxls

- *Pixel Dimensions for Tailwind CSS*

This plugin allows you to quickly generate pixel classes for Tailwind CSS.

## Requirements

This plugin requires Tailwind CSS 2.2.2 or later.

## Installation

```bash
yarn add proto-tailwindcss-pxls
```

## Usage

The following plugin options are available. See below how these are passed (via an object) to the plugin in your `tailwind.config.js`.

## Supported Tags

This plugin currently support the following tags in Options:

```
const tags = [
  'fontSize',
  'height',
  'lineHeight',
  'maxHeight',
  'maxWidth',
  'minHeight',
  'minWidth',
  'spacing',
  'width',
]
```

Specifying any of those in options will generate pixel classes as shown below.

> CAVEAT:  if you want the full 900 pixel variations to be generated, you have to pass an empty object in the options:
>
> ```
> width: {},
> ```
>
> The plugin no longer generates width & height by default, you must specify which tags you want to generate...

## Options Available

You can pass along number values to define the range of the generated sizes.

```
  start: number,  // defaults to 0
   stop: number,  // defaults to 900
```

For example:

```js
// tailwind.config.js
module.exports = {
  plugins: [
    // Generate 10 widths and 3 heights in pxs
    require('proto-tailwindcss-pxls')({
        width: {
          stop: 10,
        },
        height: {
          stop: 10,
          start: 8,
        },
    }),
  ],
};
```

The above configuration would roughly generate the following CSS:

```css
.w-0px {
  width: 0;
}

.w-1px {
  width: 1px;
}

.w-2px {
  width: 2px;
}

.w-3px {
  width: 3px;
}

.w-4px {
  width: 4px;
}

.w-5px {
  width: 5px;
}

.w-6px {
  width: 6px;
}

.w-7px {
  width: 7px;
}

.w-8px {
  width: 8px;
}

.w-9px {
  width: 9px;
}

.w-10px {
  width: 10px;
}

.h-8px {
  height: 8px;
}

.h-9px {
  height: 9px;
}

.h-10px {
  height: 10px;
}
/* etc. */
```

Which you can then use in your HTML like this:

```html
<div class="h-10px">
  I'm a div with a height of 10 pixels or pickles depending on how you pronounce it.
</div>
```

The above depends on the order of the generated CSS.
