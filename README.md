# Compare sorting speeds across languages

This repository benchmarks the same sorting dominated workflow in several programming
languages.

Consider a vector $V$ of $n$ random numbers uniformly distributed between $0$ and $1$. What
is the expectation value of the dot product of $V$ and $1, 2, 3, \dots, n$? What if we sort
$V$ first? For each language, I implement a straightforward approximation algorithm for each
task. The first algorithm samples random vectors and computes dot products. The second is
the same with an additional sort operation between generation and dot product. Implementations are in [src](src).

I compute the difference between runtime with and without sorting to infer the sorting
runtime. For high performing languages on this benchmark, the vast majority of the time is
spent sorting (typically 80-90%).

I choose to use a sorting heavy workflow rather than simpler microbenchmarks to increase
fairness across languages and benchmarking styles. By running each workflow on the order of
a second, benchmarking artifacts are greatly reduced.

Some languages are given more numbers to sort than other languages, but these differences
are canceled by differences in speed resulting in a similar amount of processing time for
each implementation.

![Julia and Java outperform other languages](figure.png)

## Limitations

This benchmark, while more realisitc than many sorting bencharks, is still a microbenchmark,
and as such may contian benchmarking artifacts different than those found in production
code.

The benchmark covers only sorting of random floating point numbers into increasing order. 
See [SortMark.jl](https://github.com/LilithHafner/SortMark.jl) for a much more diverse set
of benchmarks for the Julia language specifically.

Each data point above is the result of a single trial. Lines would be smoother and more
reproducible if they were computed as a mean or median of three trials. Taking this to an
extreme, however, is likely to reintroduce benchmarking artifacts.