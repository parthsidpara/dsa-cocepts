Bitmasking - technique used to manipulate individual bits of data using bitwise operations.
Like putting on a specific filter/mask to select/modify/check certain bits in a binary sequence.

## Bitwise Logic Operations

| Operation   | Symbol | Description                       |
| ----------- | ------ | --------------------------------- |
| AND         | `&`    | Bitwise AND of two values         |
| OR          | \|     | Bitwise OR of two values          |
| XOR         | `^`    | Bitwise XOR of two values         |
| NOT         | `~`    | Bitwise NOT (complement)          |
| Left shift  | `<<`   | Shift bits left (multiply by 2^n) |
| Right shift | `>>`   | Shift bits right (divide by 2^n)  |

## Basic Bitmask Operations

| Operation        | Syntax (C-like)            | Description                       |
| ---------------- | -------------------------- | --------------------------------- |
| Set bit          | `x \|= (1 << n)`           | Sets the nth bit to 1             |
| Clear bit        | `x &= ~(1 << n)`           | Sets the nth bit to 0             |
| Toggle bit       | `x ^= (1 << n)`            | Flips the nth bit                 |
| Check bit        | `(x & (1 << n)) != 0`      | Tests if nth bit is set           |
| Extract last bit | `x & -x` or `x & (~x + 1)` | Gets the rightmost set bit        |
| Remove last bit  | `x & (x - 1)`              | Clears the rightmost set bit      |
| Set all bits     | `~0`                       | Creates a value with all bits set |

## Common Bitmask Techniques

| Technique                      | Syntax                                     | Description                        |
| ------------------------------ | ------------------------------------------ | ---------------------------------- |
| Count set bits                 | `__builtin_popcount(x)` (GCC)              | Counts the number of 1 bits        |
| Check if power of 2            | `x && !(x & (x - 1))`                      | Tests if exactly one bit is set    |
| Next power of 2                | `x ? 1 << (32 - __builtin_clz(x - 1)) : 1` | Next higher power of 2             |
| Iterate over subsets           | `for(int s=m; s; s=(s-1)&m)`               | Loop through all subsets of mask m |
| Enumerate all subsets          | `for(int s=0; s<(1<<n); s++)`              | Loop through all 2^n subsets       |

## Common Bitmask Applications

|Application|Description|
|---|---|
|Subset representation|Use bits to represent presence/absence in a set|
|State compression|Encode multiple boolean states in a single integer|
|Efficient set operations|Perform set operations (union, intersection) with bitwise operators|
|Dynamic programming|Use bitmasks for state representation in DP problems|
|Permission systems|Encode user/system permissions as bit flags|

## Example Usage Patterns

```
// Set operations on a set represented as a bitmask
int union_set = set1 | set2;
int intersection_set = set1 & set2;
int difference_set = set1 & ~set2;
bool is_subset = (set1 & set2) == set1;

// Iterate through all subsets of {0,1,2,...,n-1}
for (int mask = 0; mask < (1 << n); mask++) {
    // Process subset represented by mask
    for (int i = 0; i < n; i++) {
        if (mask & (1 << i)) {
            // i is in the subset
        }
    }
}
```

### Swapping Two Bits

```c
if (((x >> i) & 1) != ((x >> j) & 1)) {
    x ^= (1 << i) | (1 << j);
}
```



---

codechef que: https://www.codechef.com/AABH2020/problems/ODTPIC
codeforces article: https://codeforces.com/blog/entry/73558

