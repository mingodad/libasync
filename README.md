﻿[![Build Status](https://travis-ci.org/etcimon/libasync.png)](https://travis-ci.org/etcimon/libasync)

About
-----

The libasync asynchroneous library (beta) is written completely in D, features a cross-platform event loop and enhanced connectivity and concurrency facilities for extremely lightweight asynchroneous tasks. It embeds naturally to D projects (version >= 2.066.0), compiles statically with your project and has an open source license (MIT).

A fully functional, tested vibe.d driver is available on [this fork](https://github.com/etcimon/vibe.d/tree/native-events).

### Features

The following capabilities are now being tested and should not be used in any circumstance in a production environment.

(*) _Tested on Mac, Linux, Windows and FreeBSD_ - Platforms used were Mac OS X (10.8), Linux (Fedora 20) and Windows (8.1), although it should be compatible to 99% of Desktop OS users.

- **Multi-threading** support - EventLoop can be launched and run from an unlimited number of threads!

- **Asynchroneous TCP connection** - handles multiple requests at a time in each individual thread

- **Asynchroneous TCP listener** - delivers a new connection to the delegate of your choice

- **File Operations** - executes file read/write/append commands in a thread pool, notifies of completion in a handler

- **DNS resolver** - runs blocking DNS resolve operations in a thread pool, savings are the duration of a ping.

- **File/Folder Watcher** - watches directories for file changes (CREATE, DELETE, MODIFY, RENAME/MOVE)

- **UDP connection** - receives or sends packets from/to multiple peers

- **Timer** - sets a periodic or one-shot/periodic timer with high-precision (μs) to call a select delegate

- **Signal** - Wakes up the event loop in a foreign thread and passes a message to its delegate

- **Notifier** - Thread-local and lock-less adaptation of **Signal** which queues a message intended for a local delegate

### Limitations

Some or all of these limitations are possibly being implemented currently and may be available in a future release.

- **One EventLoop per thread** - There is a hard limit of one event loop per thread
- **Futures and Promises** - Call chaining is not supported yet, however a vibe.d driver is available on my fork
- **Manual error management** - The entire library is `nothrow` and error management must be built on top of it.

Installation Instructions
-------------------------

- Download and install DMD 2.066.0+ from [dlang.org](http://dlang.org/download.html)
- Download and install dub 0.9.22-rc.2+ from [code.dlang.org](http://code.dlang.org/download)
- Use Git to clone this repository
- Run `dub test` to test the library on your operating system (submit any issue with a log report by uncommenting `enum LOG = true` in `types.d`)
- Add the library to your project by including it in the dependencies, using `import libasync.all`
- The recommended editor is MonoDevelop with [Mono-D](http://wiki.dlang.org/Mono-D) due to its Mixin Template resolver (must be enabled manually), with auto-completion and comment-resolved summary tooltips.

Tutorial
--------

Only 2 examples are available at the moment, they are located in `examples/tcp_listener` and `examples/tcp_client`. They must be tested by starting the server before the client.

All current usage examples are available in `source/libasync/test.d`. 

Documentation has been written thoughout the code.
