# mod_grpcbackend

This module provides a way for apache to directly interact with a grpc backend service. Using this you can add a webinterface to your grpc service without any additional libraries or complex configuration.

### Building

In order to build mod_grpcbackend on your system you need to install some required packages:
* build-essential
* protoc
* libprotobuf
* libgrpc++
* apache2-dev

If you have installed all required software checkout this repository and run

`make`

`make install`

and add the following line somewhere in your apache config:

`LoadModule grpcbackend_module /usr/lib/apache2/modules/mod_grpcbackend.so`

### Configuration

Currently mod_grpcbackend provides only 4 configuration directives, but only 2 are required for a working configuration. In addition to enabling grpcbackend using `GrpcEnabled` you need to set the handler to `grpcbackend` if you want a file to get handled by grpcbackend. See [SetHandler](https://httpd.apache.org/docs/current/mod/core.html#sethandler) and [AddHandler](https://httpd.apache.org/docs/2.4/de/mod/mod_mime.html#addhandler) for more information.

##### GrpcEnabled Directive

If you want a directory to be handled by a grpc backend, you need to set this directive to on.

##### GrpcHost Directive

This allows you to set the grpc service host and port apache will forward your requests to.

##### GrpcConnectTimeout Directive

This optional directive allows you to set a timeout in milliseconds for connecting to your backend service.

##### GrpcCallTimeout Directive

This optional directive allows you to set a timeout in milliseconds for each call to your backend service.

