# FluentD

FluentD logs collector with 2 extra plugins:

1. fluent-plugin-**gelf-hs** (for logs export to GrayLog instance, UDP connection confirmed) and
2. fluent-plugin-**concat** (for handling multiline logs)

This image is based on **FluentD v1.11.5-1.0**.

Start your dockerized FluentD instance like this:

```
docker run -d -p 24224:24224 \
-v $WORKDIR/fluentd/fluentd.conf:/fluentd/etc/fd.conf \
-e FLUENTD_CONF=fd.conf \
emergn/fluentd
```
Use `-it` instead of `-d` option to see the console (debug) output.

Default port: 24224

Prebuilt Docker image is available at: https://hub.docker.com/r/emergn/fluentd


## Sample configuration

For sample configuration file, see `fluentd/fluentd.conf`

To collect Docker logs from particular process, start the Docker process like this (check "log-" options):

```
docker run -it --log-driver=fluentd --log-opt tag="mycontainer1" --log-opt fluentd-address=localhost:24224 --log-opt fluentd-async-connect="true" --network=host mydockerimage
```


eof