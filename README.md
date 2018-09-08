# GoRx
*ReactiveX* is a new, alternative way of asynchronous programming to callbacks, promises and deferred. It is about processing streams of events or items, with events being any occurrences or changes within the system.

[doc](https://godoc.org/github.com/langhuihui/GoRx/pipe)
# usage

GoRx's usage is very like RxJs. However implemention by Golang is very different with Javascript

## traditional usage
in tradition we call `Chain programming`
just like rxjs 5.0
```go
import "github.com/langhuihui/gorx"
rx.Interval(1000).SkipUntil(rx.Of(1).Delay(3000)).Subscribe(func(x interface{}, dispose func()) {
		fmt.Print(x)
	}, nil, nil)
```

## pipe usage

just like rxjs 6.0,but there are still some difference.

```go
import . "github.com/langhuihui/gorx/pipe"
Subscribe(func(x interface{}, dispose func()) {
		fmt.Print(x)
	}, nil, nil)(Interval(1000),SkipUntil(Of(1),Delay(3000)))
```

## Concept
An `Observable` is a synchronous stream of "emitted" values which can be either an empty interface{} or error. Below is how an `Observable` can be visualized:

```bash

                                time -->

(*)-------------(o)--------------(o)---------------(x)----------------|>
 |               |                |                 |                 |
Start          value            value             error              Done

```

