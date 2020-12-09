# FluentD

FluentD logs collector with extra plugins:

- fluent-plugin-gelf (for logs export to GrayLog instance)
- fluent-plugin-concat (for handling multiline logs)

This image is based on **FluentD v1.11.5-1.0**.

Start your dockerized FluentD instance like this:

```
docker run -it -p 24224:24224 \
-v $WORKDIR/fluentd/fluentd.conf:/fluentd/etc/fd.conf \
-e FLUENTD_CONF=fd.conf \
fluentdd
```

Using default port: 24224.

eof