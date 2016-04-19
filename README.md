# ratpack-zipkin

![Build status](https://travis-ci.org/hyleung/ratpack-zipkin.svg?branch=master)

[Zipkin](https://twitter.github.io/zipkin/index.html) support for [Ratpack](http://www.ratpack.io).

This repo is a work-in-progress for adding Zipkin support to Ratpack.

Uses [Brave](https://github.com/openzipkin/brave) for the underlying Zipkin support.

## Getting Started

The mimimal configuration:

```
RatpackServer.start(server -> server
    .serverConfig(config -> config.port(serverPort))
    .registry(Guice.registry(binding -> binding
        .module(ServerTracingModule.class, config -> config.serviceName("some-service-name")
        .bind(HelloWorldHandler.class)
    ))(
    .handlers(chain -> chain
        ...)
);
```

This should add a `HandlerDecorator` that adds server send (SS) and server receive (SS) tracing using the default settings.
