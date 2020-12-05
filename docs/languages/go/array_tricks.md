---
title: Array tricks
authors:
    - Alexander Serowy
---

## Filtering without allocating

This trick uses the fact that a slice shares the same backing array and capacity as the original, so the storage is reused for the filtered slice. Of course, the original contents are modified.

```go
b := a[:0]
for _, x := range a {
    if f(x) {
        b = append(b, x)
    }
}
```

## Reversing

To replace the contents of a slice with the same elements but in reverse order:

```go

for i := len(a)/2-1; i >= 0; i-- {
    opp := len(a)-1-i
    a[i], a[opp] = a[opp], a[i]
}
```

The same thing, except with two indices:

```go
for left, right := 0, len(a)-1; left < right; left, right = left+1, right-1 {
    a[left], a[right] = a[right], a[left]
}
```

## Shuffling

Implementation of Fisher–Yates algorithm:

```go
for i := len(a) - 1; i > 0; i-- {
    j := rand.Intn(i + 1)
    a[i], a[j] = a[j], a[i]
}
```
