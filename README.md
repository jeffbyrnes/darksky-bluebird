# darksky-bluebird
[![js-semistandard-style](https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semistandard)

Wrapper for the [Dark Sky API](https://darksky.net/dev/)

Only dependency is Bluebird!

Here's how to use it:

Require the module:

```javascript
var Forecast = require('darksky-bluebird');
```

Instantiate an instance of the wrapper.  You'll need to specify your API key.  You may also supply your own `timeout` value, which defaults to 2000ms or 2 seconds if not provided.

```javascript
var forecast = new Forecast({
  key: process.env.DARK_SKY_API_KEY,
  timeout: 2500
});
```

To fetch a forecast for the current time:

```javascript
forecast.fetch(latitude, longitude)
  .then(function (result) {
    console.dir(result);
  })
  .catch(function (error) {
    console.error(error);
  });
```

To fetch a forecast for a specific time:

```javascript
var time = new Date().setDate(32);

forecast.fetch(latitude, longitude, time)
  .then(function (result) {
    console.dir(result);
  })
  .catch(function (error) {
    console.error(error);
  });
```

To fetch a forecast for the current time with any of the "options" specified on the documentation page:

```javascript
var options = {
  extend: 'hourly',
  units: 'auto'
};

forecast.fetch(latitude, longitude, options)
  .then(function (result) {
    console.dir(result);
  })
  .catch(function (error) {
    console.error(error);
  });
```

To fetch a forecast for a specific time with additional "options" from the documentation page:

```javascript
var time = new Date().setDate(32);
var options = {
  units: 'si',
  exclude: 'hourly,minitely',
  lang: 'x-pig-latin'
};

forecast.fetch(latitude, longitude, time, options)
  .then(function (result) {
    console.dir(result);
  })
  .catch(function (error) {
    console.error(error);
  });
```

That's it folks!  Now go build something awesome!
