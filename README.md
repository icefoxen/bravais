# bravais

A Rust library for manipulating matrices of numbers, a la numpy.

Currently just an idea.  If nothing useful is here and you want the cargo name,
message me on github.

# The shape of things

The main goal here is to have something for easily slicing, mixing, and manipulating datasets of all sorts
of shapes, sizes and arities.

 * General-purpose, N-dimensional arrays a la numpy
  * Dense vs. sparse
  * Heterogenous vs. homogenous
  * Data types: Integer, float, character, string, other (categorical data!)
  * Make a very general-purpose structure or interface and then specialize it to the 
  * Assume it's all going to be on the heap; no need for nalgebra-like super-specialization-magic here.
  * bignums?  Ponder it.  Look at the options.
  * Ideally should be easy to interface with C code, perhaps bridges with R and Python, gluon?  This implies also not going
    balls-out with generics.
  * Probably going to be trait-object-y as all hell?
 * A slice or view of such an array
  * Can vary shape, size, etc. of the underlying data
  * Probably borrowed, maybe can be Rc'ed or Cow
 * Timeseries data
  * Again, dense or sparse, a la SSTS
  * Temporal queries need to be easy dammit
 * Metadata 
  * It should be possible to tag arrays with metadata, or extract the underlying info to strip the metadata
  * Row/column names, types, relations/invariants,
  * Really I want to be able to just tell the system what TYPE of transformation I want on my data and have it do it
  * One of my constant frustrations with numpy is it's often very hard to slice things *just right* to communicate some
    little semantic details of your data...
 * Algorithms
  * There'll be shittons of these and they should be fairly easy to add on more; compare basic numpy vs. scipy
  * Very basic and fundamental stuff like addition, subtraction, comparison, filtering, basic statistics should always be there
 * Data reading/writing
  * Definitely: CSV, image, sqlite
  * Maybe: HDF5, geotiff, what else?  Geospatial types?

# Related problems

 * Graphing!  lyon gives nice drawing primitives.
 * Statistics, algorithms, etc.  Equivalent to scipy.  Someone else's problem.
 * Data structures that don't fit into memory.  Would be nice to allow someone else's crate to present a uniform interface
   using this.

# References

https://docs.scipy.org/doc/numpy/reference/

# Related crates to look closer at!

Data structures

 * https://github.com/bluss/rust-ndarray

Algorithms

 * https://github.com/indigits/scirust
 * https://crates.io/crates/rustml

Plotting

 * https://crates.io/crates/dataplotlib
 * https://github.com/japaric/criterion.rs has a plotting library
