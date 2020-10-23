<h1 align="center">Welcome to socketiotest 👋</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-1.0.0-blue.svg?cacheSeconds=2592000" />
  <a href="#" target="_blank">
    <img alt="License: ISC" src="https://img.shields.io/badge/License-ISC-yellow.svg" />
  </a>
  <a href="https://twitter.com/alois\_hias" target="_blank">
    <img alt="Twitter: alois\_hias" src="https://img.shields.io/twitter/follow/alois\_hias.svg?style=social" />
  </a>
</p>

> socket.io introduction

# In index.js

```javascript
io.emit('some event', { someProperty: 'some value', otherProperty: 'other value' }); // This will emit the event to all connected sockets

io.on('connection', (socket) => {
  socket.broadcast.emit('hi');
});

io.on('connection', (socket) => {
  socket.on('chat message', (msg) => {
    io.emit('chat message', msg);
  });
});
```

# In index.html

```html
<script>
  $(function () {
    var socket = io();
    $('form').submit(function(e){
      e.preventDefault(); // prevents page reloading
      socket.emit('chat message', $('#m').val());
      $('#m').val('');
      return false;
    });
    socket.on('chat message', function(msg){
      $('#messages').append($('<li>').text(msg));
    });
  });
</script>
```

## Install

```sh
npm i
```

## Usage

```sh
npm run dev
```

## Run tests

```sh
npm run test
```

## Author

👤 **Aloïs HIAS**

* Twitter: [@alois\_hias](https://twitter.com/alois\_hias)
* Github: [@aloishias](https://github.com/aloishias)

## Show your support

Give a ⭐️ if this project helped you!

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_