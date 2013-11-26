Priority Queue
==============

In memory queue system prioritizing tasks.


Documentation
=============

Installation
-------------

``` bash
$ npm install --save priority-queue
```

Methods
------------

### Constructor

The constructor take an optionnal array of prioritized tasks. The first `String` name will be the first queue to be emptied, the second in second, etc.

``` javascript
var Queue = require('priority-queue');

var queue = new Queue([ 'first', 'second', 'third' ]);
```

### Queue#add `add( [priority], task )`

Add a task into a queue with optionnal priority. If no priority is specified, `default` (the least priority) will be use.

Implicitly, each time you add a task, the queue will start running (if not already running).

Each tasks runned in the queue will receive a callback function to call once finished.

``` javascript
queue.add(function( cb ) {
  DB.fetch().then( cb );
});
```

#### Pro tip

Bind your tasks with context and arguments!

``` javascript
var task = function( models, cb ) {
  /* you get `models` data here! */
};
queue.add( task.bind(null, models) );
```

### That's all?

Yes!


Todos
==========

+ Add named task support to prevent duplicate tasks to be runned
+ Allow sub-queues to run multiple tasks concurrently


Contributing
=====================

**Style Guide**: Please base yourself on [Idiomatic.js](https://github.com/rwldrn/idiomatic.js) style guide with two space indent  
**Unit test**: Unit test are wrote in Mocha. Please add a unit test for every new feature
or bug fix. `npm test` to run the test suite.  
**Documentation**: Add documentation for every API change. Feel free to send corrections
or better docs!  
**Pull Requests**: Send _fixes_ PR on the `master` branch. Any new features should be send on the `wip`branch.


License
=====================

Copyright (c) 2012 Simon Boudrias (twitter: @vaxilart)  
Licensed under the MIT license.