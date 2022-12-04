# Blabble Server

A cloud data server for Scratch 3.0, configured and optimized for Blabble.

It uses a protocol very similar to Scratch 3's cloud variable protocol. See doc/protocol.md for further details.

## IMPORTANT

No being sussy baka or you will b baned from our blalbbe server for sus reason so be very very nice and no sussy at all.

## Restrictions

This server does not implement long term variable storage. All data is stored only in memory (never on disk) and are removed promptly when rooms are emptied or the server restarts.

This server also does not implement chat logs.

## Setup

Needs Node.js and npm.

```
git clone https://github.com/Dogo6647/blabble-server
cd blabble-server
npm install
npm start
```

By default the server is listening on ws://localhost:8148/ (BLAB in 1337speak). To change the port, read below.

You can change the target server URL for your custom Blabble client in the TurboWarp Packager settings.

!! DON'T use Mr. Garbo's official TurboWarp servers. He will not be happy. !!


## Configuration

HTTP requests are served static files in the `public` directory.

### src/config.js

src/config.js is the configuration file for Blabble server.

The `port` property (or the `PORT` environment variable) configures the port to listen on.

On unix-like systems, port can also be a path to a unix socket. By default cloud-server will set the permission of unix sockets to `777`. This can be configured with `unixSocketPermissions`.

If you use a reverse proxy, set the `trustProxy` property (or `TRUST_PROXY` environment variable) to `true` so that logs contain the user's IP address instead of your proxy's.

Set `anonymizeAddresses` to `true` if you don't need to doxx people.

Set `perMessageDeflate` to an object to enable "permessage-deflate", which uses compression to reduce the bandwidth of data transfers. This can lead to poor performance and catastrophic memory fragmentation on Linux (https://github.com/nodejs/node/issues/8871). See here for options: https://github.com/websockets/ws/blob/master/doc/ws.md#new-websocketserveroptions-callback (look for `perMessageDeflate`)

You can configure logging with the `logging` property of src/config.js. By default cloud-server logs to stdout and to files in the `logs` folder. stdout logging can be disabled by setting `logging.console` to false. File logging is configured with `logging.rotation`, see here for options: https://github.com/winstonjs/winston-daily-rotate-file#options. Set to false to disable.
