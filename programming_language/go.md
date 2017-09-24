# Notes on Go programming language

## Course

1. [Distributed Systems](https://pdos.csail.mit.edu/6.824/schedule.html)

## Frameworks 

1. [Goriall](http://www.gorillatoolkit.org/)
1. [Beego](https://beego.me/)
1. [Revel](http://revel.github.io/)
1. [Martini](http://martini.codegangsta.io/)
1. [Gocraft](https://github.com/gocraft/web)

## References

1. [Tour of Go](https://tour.golang.org/welcome/1)
1. [How to write Go Code](https://golang.org/doc/code.html)
1. [Golang FAQs](https://golang.org/doc/faq)
1. [Go by Example](https://gobyexample.com/)
1. [Go Language Patterns](http://www.golangpatterns.info/)
1. [Effective Go](https://golang.org/doc/effective_go.html)

## Blog Articles

1. [About Go Language — An Overview](https://hackernoon.com/about-go-language-an-overview-bba4b04f454b)
1. [Getting started with WebSockets in Go](https://blog.codeship.com/getting-started-with-websockets-in-go/)
1. [Ultimate guide to writing Go tool](https://t.co/NICV3z6PP2)
1. [tinynet: A lightweight instant virtual network for rapid prototyping SDN]()

## Videos & Conferences

1. [Golang Chat Server](https://www.youtube.com/watch?v=cNxfgXrHeAg)
1. [Go for Pythonista](https://www.youtube.com/watch?v=elu0VpLzJL8)
1. [Go: object oriented and concurrent](https://www.youtube.com/watch?v=Ng8m5VXsn8Q)
1. [Using WebSocket in Go](https://www.youtube.com/watch?v=CIh8qN7LO8M)
1. [Golang UK 2017](https://www.youtube.com/channel/UC9ZNrGdT2aAdrNbX78lbNlQ/videos)
1. [GopherVideos](https://gophervids.appspot.com/)
1. [GopherCon 2014 Writing and Debugging a Web-Based Multi-Player Game](https://www.youtube.com/watch?v=PJlp1YacstQ&t=444s)

## Summary of [Go Concurrency Patterns](https://www.youtube.com/watch?v=f6kdp27TYZs)

1. [Slides](https://talks.golang.org/2012/concurrency.slide#1)
1. Concurrency is way to structure software, particularly as a way to write clean code that interacts well with the world
1. It is not parallelism
1. Erlang is closed to Communicating Sequential Processes Paper, where you communicate to a process by name rather than over channel
1. Go is distinguised by first class channels
1. Roughly analogous to:
    1. Writing to a file by name {Erlang}
    1. Writing to a file descriptor {Golang}
1. Think about go routine as a simple shell command with `&` at the end of the line
1. Go feature when `main` returns program exits
1. Go routines are {extremely cheap threads}
    - Independently executing functions {don't want to wait for answer to comeback}
    - It has its own class stack which grows and shrinks according to its needs
    - It's very cheap. It is practical to have thousands, even tens of thousands of goroutine
    - Go routines are multiplexed dynamically onto threads
1. A channel in Go provides a connection between two go routines, allowing them to communicate
    - Creating channel `c := make(chan int)`
    - Sending on a channel `c <- 7`
    - Recieving on a channel `value = <-c`
    - Both sending and recieving on a channel are blocking {this is equivalent of lock step/synchronization operation}
1. Buffered channels are non-blocking {Just fetch/drop from a buffer}
    - More like mailboxes in Erlang
1. Don't communicate by shaing memory, share memory by communicating
1. Concurrency Patterns {Tiny examples than a formal}
    - Generator {Function that returns a channel}
        - Channels are first-class values just like strings or integrers
        - Very much like a service
    - Fan-in allows better co-ordination
        - Takes two channels as input and output one channel
    - You can pass a channel into another channel
    - Wait channel acts as signals {asking for communicating process to wait}
1. `select` is a control structure unique to concurrency {similar to `switch` statement. This is like a `guard` from Dijkstra}
    - Allows to change behaviour of the program
    - It evaluates all channels on which communication is possible. It blocks until there is communication on one of the channels
    - Also has a `default` block
    - If communication is avilable on multiple channels, `select` chooses psuedo-randomly
1. `time.After` will allow us to implement timeout operation on a go routine
1. `quit` channel is also possible
1. Word of caution
    - Don't overuse it
    - Go has `sync` and `sync/atomic` is reference counting {which is sometimes more than enough}

## Summary of [Rob Pike - 'Concurrency Is Not Parallelism'](https://www.youtube.com/watch?v=cN_DpYBzKso)

1. [Slides](https://talks.golang.org/2012/waza.slide#1)
1. Concurrency and Parallel is not the same
1. What is Concurrency?
    - Way to build things {Set of independently executing things}
    - Dealing a lot of things at once
    - E.g. OS Kenel has to manage {Keyboard, Mouse, Diplay and Processor} CONCURRENTLY
    - About Structure
1. What is Parallelism?
    - Excuting the same thing in parallel {possibly related or not}
    - Doing a lot of things at once
    - Vector Product {Divide elements into smaller parts and do it all at once}
    - About Execution
1. Observations
    - Adding things to design can make it more efficient
    - If you get concurrency right, parallelism {kind of falls into place}
1. Talks a great analogy of web-serving architecture {as means of gopher working on destroying pile of book}
1. `for x := range input`, `range` here drains the channel until it runs out of messages
1. Great load-balancer of work on [slide 41](https://talks.golang.org/2012/waza.slide#41). Think Producer/Cosumer pattern
1. Pass channel with Request {think of channels as file descriptors}
1. Concurrency enable parallelism