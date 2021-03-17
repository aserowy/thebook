---
title: Array Operations
authors:
  - Alexander Serowy
---

## AppendVector

```go
a = append(a, b...)
```

## Copy

```go
b = make([]T, len(a))
copy(b, a)
// or
b = append([]T(nil), a...)
```

## Cut

```go
a = append(a[:i], a[j:]...)
```

> To ensure gc of structs with pointer fields or pointer as elements and prevent possible memory leaks use the following.

```go
copy(a[i:], a[j:])
for k, n := len(a)-j+i, len(a); k < n; k++ {
    a[k] = nil // or the zero value of T
}
a = a[:len(a)-j+i]
```

## Delete

```go
a = append(a[:i], a[i+1:]...)
// or
a = a[:i+copy(a[i:], a[i+1:])]
```

> To ensure gc of structs with pointer fields or pointer as elements and prevent possible memory leaks use the following.

```go
copy(a[i:], a[i+1:])
a[len(a)-1] = nil // or the zero value of T
a = a[:len(a)-1]
```

## Delete without preserving order

```go
a[i] = a[len(a)-1]
a = a[:len(a)-1]
```

> To ensure gc of structs with pointer fields or pointer as elements and prevent possible memory leaks use the following.

```go
a[i] = a[len(a)-1]
a[len(a)-1] = nil
a = a[:len(a)-1]
```

## Expand

```go
a = append(a[:i], append(make([]T, j), a[i:]...)...)
```

## Extend

```go
a = append(a, make([]T, j)...)
```

## Insert

```go
a = append(a[:i], append([]T{x}, a[i:]...)...)
```

> The second append creates a new slice with its own underlying storage and copies elements in a[i:] to that slice, and these elements are then copied back to slice a (by the first append). The creation of the new slice (and thus memory garbage) and the second copy can be avoided by using an alternative way:

```go
s = append(s, 0)
copy(s[i+1:], s[i:])
s[i] = x
```

## InsertVector

```go
a = append(a[:i], append(b, a[i:]...)...)
```

## Pop

```go
x, a = a[0], a[1:]
```

## Pop Back

```go
x, a = a[len(a)-1], a[:len(a)-1]
```

## Push

```go
a = append(a, x)
```

## PushFront

```go
a = append([]T{ x }, a...)
```

## Shift

```go
x, a := a[0], a[1:]
```

## Unshift

```go
a = append([]T{x}, a...)
```
