# Laravel Echo Server

NodeJs server for Laravel Echo broadcasting with Socket.io.

## System Requirements

The following are required to function properly.

*   Laravel 5.3
*   Node 6.0+
*   Redis 3+

Additional information on broadcasting with Laravel can be found on the
official docs: <https://laravel.com/docs/master/broadcasting>

## Getting Started

Install npm package in your project directory.

``` shell

$   npm install laravel-echo-server --save

```

### Initialize with CLI Tool

Run the init command.

``` shell

$   laravel-echo-server init

```

The cli tool will help you setup a **laravel-echo-sever.json** file in the root directory of your project. This file will be loaded by the server during start up. You may edit this file later on to edit your configuration.

### Configurable Options

Edit the default configuration of the server.

``` javascript
var echo = require('laravel-echo-server');

var options = {
  authHost: 'http://app.dev',
  authPath: '/broadcasting/auth',
  host: 'http://app.dev',
  port: 6001,
  sslCertPath: '/path/to/app.dev.cert',
  sslKeyPath: '/path/to/app.dev.key'
};

echo.run(options);
```

| Title          | Default        | Description |
| :------------- | :------------- | :-----------|
| `appKey`       | `string`       | Unique app key used in security implementations. |
| `authHost`     | `http://localhost` | The host of the server that authenticates private and presence channels  |
| `authPath`     | `/broadcasting/auth` | The route that authenticates private channels  |
| `hostname`     | `http://localhost` | The host of the socket.io server |
| `port`         | `6001`         | The port that the socket.io server should run on |
| `sslCertPath`  | `string`       | The path to your server's ssl certificate |
| `sslKeyPath`   | `string`       | The path to your server's ssl key |

### Running with SSL

*   Your client side implementation must acccess the socket.io client from https.

*   The server configuration must set the server host to use https.
*   The server configuration should include paths to your ssl certificate and key located on your server.

*Note: This library currently supports only serving from either http or https, not both.*

## Client Side Configuration

See the offical Laravel documentation for more information. <https://laravel.com/docs/5.3/broadcasting#introduction>

### Tips

You can include the socket.io client libray from your running server.
For example, if your server is running at `app.dev:6001` you should be able to
add a script tag to your html like so:

`<script src="//app.dev:6001/socket.io/socket.io.js"></script>`
