# React Instascan
## Port of [Instascan](https://github.com/schmich/instascan) library to React  
[![Build Status](https://travis-ci.org/rubenspgcavalcante/react-instascan.svg?branch=master)](https://travis-ci.org/rubenspgcavalcante/react-instascan)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/639bf0dfa90f47b280f31e7498a40f5a)](https://www.codacy.com/app/rubenspgcavalcante/react-instascan?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=rubenspgcavalcante/react-instascan&amp;utm_campaign=Badge_Grade)
[![Codacy Badge](https://api.codacy.com/project/badge/Coverage/639bf0dfa90f47b280f31e7498a40f5a)](https://www.codacy.com/app/rubenspgcavalcante/react-instascan?utm_source=github.com&utm_medium=referral&utm_content=rubenspgcavalcante/react-instascan&utm_campaign=Badge_Coverage)
[![npm version](https://badge.fury.io/js/react-instascan.svg)](https://badge.fury.io/js/react-instascan)
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)

# Warning
This library is using `instascan-umd` instead of `instascan` as a per-dependencie.
If you're upgrading for newer verions you must install `istascan-umd`.

# Installing
**npm**   
```bash
npm install react-instascan react instascan-umd --save
```

**yarn**  
```bash
yarn add react-instascan react instascan-umd
```

**Using unpkg CDN**
```html
<script type="application/javascript" src="https://unpkg.com/react-instascan/dist/main.js"></script>
```

## Requirements
To use this library you need at least:
 - react >= 16
 - instascan-umd >= 1

# Using it

## Importing
React Instascan exposes two Components: **Cameras** and **Scanner**.  
With ESModules:
```js
import { Cameras, Scanner } from "react-instascan";
```
or with CommonsJS:
```js
const { Cameras, Scanner } = require("react-instascan");
```

The "Cameras" component with a [render prop](https://reactjs.org/docs/render-props.html) and will fetch for the 
available cameras on your device.  
The Scanner Component receives as props the *camera* and a [**VideoHTMLElement**](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) 
as child element. Then it will call the *onScan* listener when reading a code. 
Other event types are also available (check the API table):
```jsx
<Cameras>
  {cameras => (
    <div>
      <h1>Scan the code!</h1>
      <Scanner camera={cameras[0]} onScan={onScan}>
        <video style={{ width: 400, height: 400 }} />
      </Scanner>
    </div>
  )}
</Cameras>
```

# Scanner properties

|      name         |         type      |                     description                   |
|-------------------|-------------------|---------------------------------------------------|
| camera            | object            | Camera object returned by \<Camera \/\>           |
| options           | object            | Same options from [Instascan.Scanner](https://github.com/schmich/instascan#let-scanner--new-instascanscanneropts)|
| stop              | boolean           | If stop is true the camera stops and vice-versa   |
| onScan            | function          | Emitted when a QR code is scanned using the camera in continuous mode |
| onStart           | function          | Called when camera is active and scanning has started |
| onStop            | function          | Called when camera and scanning have stopped |
| onActive          | function          | Emitted when the scanner becomes active as the result of stop becoming false or the tab gaining focus |
| onInactive        | function          | Emitted when the scanner becomes inactive as the result of stop becoming true or the tab losing focus |

For more details check the [Instascan API](https://github.com/schmich/instascan#api)

# Contributing

## Using directly from the source

Although this project comes with a simple example, you may want to use this code
directly on your code to test and fix possibly bugs. For that you can just link this package
```
yarn link
```

Go to your project root (where the `package.json` of your app is) and then use the linked version:
```
yarn link react-instascan
```

Now just start the build process on watch mode and you're going to see real time changes
in your project
```
yarn build --watch
```

For more information about contributing see the [CONTRIBUTING](.github/CONTRIBUTING.md) guidelines

# License

This project is under the [MIT License](https://opensource.org/licenses/MIT)
