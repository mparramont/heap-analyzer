# Not Very Good MRI Heap Analyzer

This is a Not Very Good heap analyzer for MRI.  It is not very good.

You can see the current version [here](http://tenderlove.github.io/heap-analyzer/).

## The Good Things

It processes MRI heap dumps in your browser.

After you upload your heap dump, it will it will show you a break down of
number of objects per type and number of allocations per generation:

![uploaded](https://github.com/tenderlove/heap-analyzer/raw/master/images/uploaded.png "After Upload")

If you click a slice of the pie, it will show you all allocations for that type
in the table below like this:

![objects](https://github.com/tenderlove/heap-analyzer/raw/master/images/click_slice.png "Click a slice")

If you click a row in the table, it will add a new table that lists the objects
that *point to* the object you clicked.

![references](https://github.com/tenderlove/heap-analyzer/raw/master/images/reference.png "Parent References")

Hovering over a row will show you the allocation location (if it's available):
![allocation location](https://github.com/tenderlove/heap-analyzer/raw/master/images/allocation_location.png "Allocation Location")

You can use any heap dumps from `ObjectSpace.dump_all`, but the index file
gives an example of dumping the heap for a Rails app.

## The Not Very Good Things

It has bugs, so please send pull requests.  It is slow, so please send pull
requests.  It doesn't look very good, so please send pull requests.

Also, please send pull requests.


## TODO

The points in the "objects allocated per generation" graph are not clickable.  I
would like to make them clickable in order to help find object leaks per generation. 

Building the giant table is pretty slow, I would like to speed that up.

When you click a row to view the objects that *point to* that object, it
inserts a new table.  Unfortunately that is very slow and doesn't look very
good.  I'd like to fix both of those problems.
