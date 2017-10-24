Parallel bitonic sort in rust
====

Uses `rayon` for parallelism and falls back on `unstable_sort` for short slices.
Only works on power-of-two arrays for now.

Benchmarks on 4-core (8 threads) Kaby Lake 3.8GHz laptop:

```
test bitonic_128          ... bench:       1,110 ns/iter (+/- 79)
test bitonic_32768        ... bench:     554,374 ns/iter (+/- 28,342)
test bitonic_65536        ... bench:   1,211,296 ns/iter (+/- 132,500)
test rayon_stable_128     ... bench:       1,743 ns/iter (+/- 85)
test rayon_stable_32768   ... bench:     445,732 ns/iter (+/- 22,396)
test rayon_stable_65536   ... bench:     884,402 ns/iter (+/- 30,717)
test rayon_unstable_128   ... bench:       1,066 ns/iter (+/- 148)
test rayon_unstable_32768 ... bench:     402,498 ns/iter (+/- 17,377)
test rayon_unstable_65536 ... bench:     748,362 ns/iter (+/- 41,358)
test std_stable_128       ... bench:       1,718 ns/iter (+/- 98)
test std_stable_32768     ... bench:   1,231,475 ns/iter (+/- 45,878)
test std_stable_65536     ... bench:   2,618,005 ns/iter (+/- 114,323)
test std_unstable_128     ... bench:       1,185 ns/iter (+/- 112)
test std_unstable_32768   ... bench:     895,112 ns/iter (+/- 80,483)
test std_unstable_65536   ... bench:   1,774,216 ns/iter (+/- 48,544)
```
