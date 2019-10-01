# Vue minesweeper

## Instalation

```
npm install vue-minesweeper
```

## Getting started

```javascript
import Vue from 'vue'; // Load vue
import App from './App'; // Load your app
import VueMinesweeper from 'vue-minesweeper';

Vue.use(VueMinesweeper); // Add the game

new Vue({
  render: h => h(App),
}).$mount('#app');
```

## Usage

Basic setup

```html
<minesweeper-game></minesweeper-game>
```

Setup your own grid and bomb.

```html
<minesweeper-game :rows="16" :cols="30" :bombs="99"></minesweeper-game>
```

## Usage with the vue cdn

Copy paste this and you can get started.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Vue minesweeper</title>
  <link rel="stylesheet" href="https://unpkg.com/vue-minesweeper/dist/VueMinesweeper.css">
</head>
<body>
    <div id="app">
      <minesweeper-game></minesweeper-game>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue"></script>
    <script src="https://unpkg.com/vue-minesweeper/dist/VueMinesweeper.umd.min.js"></script>
    <script>
      var app = new Vue();
      app.$mount("#app");
    </script>
</body>
</html>
```