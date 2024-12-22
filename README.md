# node-unix-stream

Communicate over UNIX datagram sockets.

## Usage

Server:

    // One-shot server.  Note that the server cannot send a reply;
    // UNIX datagram sockets are unconnected and the client is not addressable.
    var unix = require('unix-stream');
    var server = unix.createSocket('unix_stream', function(buf) {
      console.log('received ' + buf);
      server.close();
    });
    server.bind('/path/to/socket');

Client:

    // Send a single message to the server.
    var message = Buffer('ping');
    var client = unix.createSocket('unix_stream');
    client.on('error', console.error);
    client.send(message, 0, message.length, '/path/to/socket');
    client.close();


## API

TODO.
