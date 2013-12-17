logging
=======

logging library in golang base on log pkg, support log level and multi handler, colorful stdout


features
--------

* support logging level and level range

* support handler filter

* support file handler

* support time rotation handler

* support size rotation handler

* support multi handlers


example
-------

```go
import "logging"
```

stdout handler:

```go
logging.StdoutHandler.SetLevel(INFO)
logging.Debug("%d, %s", 1, "OK")
logging.Error("%d, %s", 1, "OK")
```

simple file handler:

```go
l, err := logging.NewSingleFileHandler("/tmp/sf.log")
if err != nil {
	panic(err)
}
logging.AddHandler("file", l)
...
```

time rotation handler:

```go
l, err := logging.NewTimeRotationHandler("/tmp/tr.log", "060102-15")
if err != nil {
	panic(err)
}
logging.AddHandler("rotation", l)
...
```

multi handler:

```go
...
logging.StdoutHandler.SetLevel(INFO)
logging.AddHandler("file", file_handler)
logging.AddHandler("rotation", rotation_handler)
...
```

size rotation handler

```go
l, err := logging.NewSizeRotationHandler("/tmp/sr.log", 1024, 5)
if err != nil {
	panic(err)
}
l.SetLevel(INFO)
logging.AddHandler("sr", l)
...
```
