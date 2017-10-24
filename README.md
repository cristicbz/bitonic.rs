Parallel bitonic sort in rust
====

Uses `rayon` for parallelism and falls back on `unstable_sort` for short slices.
Only works on power-of-two arrays for now.

Benchmarks on 4-core (8 threads) Kaby Lake 3.8GHz laptop:

```
running 9 tests
test std_bitonic_128    ... bench:       1,211 ns/iter (+/- 73)
test std_bitonic_32768  ... bench:     630,865 ns/iter (+/- 90,803)
test std_bitonic_65536  ... bench:   1,373,111 ns/iter (+/- 78,431)

test std_stable_128     ... bench:       1,721 ns/iter (+/- 109)
test std_stable_32768   ... bench:   1,234,859 ns/iter (+/- 150,314)
test std_stable_65536   ... bench:   2,603,823 ns/iter (+/- 151,850)

test std_unstable_128   ... bench:       1,211 ns/iter (+/- 184)
test std_unstable_32768 ... bench:     878,739 ns/iter (+/- 51,668)
test std_unstable_65536 ... bench:   1,721,517 ns/iter (+/- 127,620)
```
