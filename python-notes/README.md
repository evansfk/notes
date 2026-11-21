# Python Built-ins & Standard Library Data Structures

Concise, executable Jupyter notebooks covering Python's core built-in containers, standard-library data structures, time complexities (CPython internals), subtle gotchas, and practical benchmarks.

## Notebooks

| Notebook | Topics Covered |
|---|---|
| [`builtin_containers.ipynb`](./builtin_containers.ipynb) | `list`, `tuple`, `dict`, `set`, `frozenset` — CPython internals, Big-O table, hashability, dict views & merge (`\|`), set algebra, and classic gotchas (mutable defaults, shallow vs. deep copy, `[[0]*3]*3`) |
| [`collections.ipynb`](./collections.ipynb) | `deque` (including bounded `maxlen` ring buffers), `Counter` (multiset arithmetic, `most_common`), `OrderedDict` (Python 3.7+ differences + $O(1)$ LRU cache), `defaultdict`, `namedtuple`, `ChainMap` |
| [`heapq.ipynb`](./heapq.ipynb) | Binary heaps & array indexing, $O(n)$ `heapify` (Floyd's algorithm), `heappushpop` vs. `heapreplace`, tuple tie-breaking with incomparable payloads, `heapq.merge`, lazy deletion, two-heap running median, and an apples-to-apples **K Closest Points** benchmark (`Min-Heap` vs. `Max-Heap` vs. `nsmallest` vs. Timsort) |
| [`itertools_and_functools.ipynb`](./itertools_and_functools.ipynb) | Lazy iteration (`chain`, `islice`, `batched`, `accumulate`, `groupby`, `product`, `combinations`) and functional tools (`lru_cache`, `partial`, `reduce`, `wraps`) |
| [`bisect_and_sorting.ipynb`](./bisect_and_sorting.ipynb) | $O(\log n)$ binary search (`bisect_left`, `bisect_right`, `key=` in 3.10+, threshold buckets) and Timsort stability & multi-key sorting (`itemgetter`) |

## Quick Big-O Reference (CPython Average Case)

| Structure | Lookup / Access | Insert / Append | Delete | Ordered? |
|---|---|---|---|---|
| `list` | $O(1)$ index / $O(n)$ `in` | $O(1)$ end / $O(n)$ front | $O(1)$ end / $O(n)$ front | Yes |
| `deque` | $O(1)$ ends / $O(n)$ middle | $O(1)$ both ends | $O(1)$ both ends | Yes |
| `dict` / `set` | $O(1)$ | $O(1)$ amortized | $O(1)$ | `dict`: insertion (3.7+) / `set`: No |
| `heapq` (on `list`) | $O(1)$ min (`h[0]`) | $O(\log n)$ push / $O(n)$ `heapify` | $O(\log n)$ `heappop` | Heap-ordered |
| Sorted `list` + `bisect` | $O(\log n)$ search | $O(n)$ `insort` | $O(n)$ | Fully sorted |

## Running Locally

All notebooks use Python 3.12+ standard library modules (only the benchmark plot at the end of `heapq.ipynb` uses `numpy` and `matplotlib`):

```bash
uv run --with jupyter --with numpy --with matplotlib jupyter lab
```
