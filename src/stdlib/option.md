---
title: Option
---

Utilities for working with the Option data type.

```grain
import Option from 'option'
```

## Values

### Option.**isSome**

```grain
isSome : Option<a> -> Bool
```

Checks if the Option is the `Some` variant.

### Option.**isNone**

```grain
isNone : Option<a> -> Bool
```

Checks if the Option is the `None` variant.

### Option.**contains**

```grain
contains : (a, Option<a>) -> Bool
```

Checks if the Option is the `Some` variant and contains the given value. Uses the generic `==` equality operator.

### Option.**expect**

```grain
expect : (String, Option<a>) -> a
```

Attempts to unwrap the inner value from the `Some` variant. If it is `None`, raises `Failure` with the provided message.

### Option.**unwrap**

```grain
unwrap : Option<a> -> a
```

Attempts to unwrap the inner value from the `Some` variant. If it is `None`, raises `Failure` with a generic message.

### Option.**unwrapWithDefault**

```grain
unwrapWithDefault : (a, Option<a>) -> a
```

Unwraps the inner value from the `Some` variant. If it is `None`, returns the default value provided.

### Option.**map**

```grain
map : (a -> b, Option<a>) -> Option<b>
```

If the Option is the `Some` variant, call `fn` with the inner value and returns a new `Some` variant with the produced value.

### Option.**mapWithDefault**

```grain
mapWithDefault : (b, a -> b, Option<a>) -> b
```

If the Option is the `Some` variant, call `fn` with the inner value and returns the result. If it is `None`, returns the default value provided.

### Option.**flatMap**

```grain
flatMap : (a -> Option<b>, Option<a>) -> Option<b>
```

If the Option is the `Some` variant, call `fn` with the inner value. The `fn` must produce its own Option to be returned.

### Option.**filter**

```grain
filter : (a -> Bool, Option<a>) -> Option<a>
```

If the Option is the `Some` variant, call `fn` with the inner value. If the `fn` returns `false`, returns a `None` variant type.

### Option.**zip**

```grain
zip : (Option<a>, Option<b>) -> Option<(a, b)>
```

If both Options are the `Some` variant, returns a new `Some` variant that contains a tuple of both values. If any of the Options are `None`, returns `None`.

### Option.**zipWith**

```grain
zipWith : ((a, b) -> c, Option<a>, Option<b>) -> Option<c>
```

If both Options are the `Some` variant, call `fn` with both inner values and returns a new `Some` variant with the produced value. If any of the Options are `None`, returns `None`.

### Option.**flatten**

```grain
flatten : Option<Option<a>> -> Option<a>
```

Flattens nested Options, like `Some(Some(1))` to `Some(1)`. If any of the Options are `None`, returns `None`.

### Option.**toList**

```grain
toList : Option<a> -> List<a>
```

If the Option is the `Some` variant, returns a `List` containing the inner value as the only item. If it is `None`, returns an empty `List`.

### Option.**toArray**

```grain
toArray : Option<a> -> Array<a>
```

If the Option is the `Some` variant, returns an `Array` containing the inner value as the only item. If it is `None`, returns an empty `Array`.

### Option.**sideEffect**

```grain
sideEffect : (a -> Void, Option<a>) -> Void
```

If the Option is the `Some` variant, call `fn` with the inner value. Always returns `void`.

### Option.**peek**

```grain
peek : (a -> Void, Option<a>) -> Option<a>
```

If the Option is the `Some` variant, call `fn` with the inner value. Always returns the Option it is called with; this method is a "chainable" `Option.sideEffect`.
