# Calculator with Currency Converter and The Weather

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Sass
`````
npm install -D sass
`````

# Calculator with currency and time converter

Create a simple calculator which should incorporate a currency converter and Time

## Project Context

Minimum requirements Calculator:
Mobil First
The calculator must be able to perform basic operations: addition, subtraction, multiplication, division
Mandatory keys:
- numerals from 0 to 9
- addition, subtraction, multiplication, division
- equal sign
- comma sign “.” for comma
- CE (to reset)

Minimum requirements Currency Converter:
Must be integrated in the calculator.
Currencies to use : Euro (€), Dollar ($), Yen (¥), Honduran Lempira (Honduras)

Minimum requirements - Weather:
The following API should be used: https://www.el-tiempo.net/api
Display an image depending on the “StateSky”.
You can choose between national or provincial (Asturias) information.

Extra:
M+ key to put in memory the current number (the local storage of the browser must be used to store the info)
MR key to retrieve the stored data
MC key to erase the data stored in memory

Stack to be used:
The application should be made with Vue 3 and optionally unit tests with Vitest. Bootstrap, Vuetify or any other CSS library can be used. Use of sass is mandatory.

Note: Installation of Vue Router and Pinia is not recommended.

### Pedagogical modalities

The project will be carried out in pair programming with role changes every 30 minutes (driver / navigator).

### Modalidades de evaluación

Se evaluará según lo indicado en el README. El README deberá ser la carta de presentación del proyecto