---
aliases:
  - Types and Polymorphism
  - Polymorphism
tags:
  - school
  - school/cs381
---
	  # Types and Polymorphism

Part of [[CS381 - Notes]]

---

![[Pasted image 20260223090404.png]]

---

## Static Typing Does NOT Evaluate the Condition

It only checks whether both branches have the same type — that's all that matters.

---

## Advantages & Disadvantages of Static vs Dynamic Typing

**Static**
- Advantages: prevents type errors
- Disadvantages: rejects some valid programs

**Dynamic**
- Advantages: detects some type errors at runtime
- Disadvantages: no guarantees, slower execution, released programs may crash unexpectedly with type errors

---

## Undecidability of Static Typing

![[Pasted image 20260223092327.png]]

Static typing (e.g. Haskell) assumes a type error when type correctness cannot be proven.

The `then` and `else` branches need to be the same type — both `Int` or both `Bool`, not one of each.

---

## Polymorphism

The use of one symbol to represent multiple types.

In C++ you can write an interface and call different functions depending on the type of the data.

---

## Subtype Polymorphism

![[Pasted image 20260223093119.png]]

We have a `virtual void` function `speak`. A class `Cat` inherits from it — because it's a virtual function, `Cat`'s version of `speak` is chosen over the base class version.

- `<T>` → same behavior, many types
- `virtual` → different behavior, same interface

---

## Parametric Polymorphism

Like in Haskell:

```haskell
-- Polymorphic function to get the first element of a list
firstElement :: [a] -> Maybe a
firstElement [] = Nothing    -- empty list
firstElement (x:_) = Just x  -- return the first element
```

`a` can be any type. Instead of locking it to `Int` or `Bool`, we use `a` as a stand-in for any type — the function works for any list regardless of what's inside it.

---

## Ad-Hoc Polymorphism

![[Pasted image 20260223094010.png]]

Similar to function overloading in C++. An **Eq class** is a group of types that support equality comparison — `Int`, `String`, lists, etc.

> Ad-hoc polymorphism refers to when a value is able to adopt any one of several types because it, or a value it uses, has been given a separate definition for each of those types.
>
> For example, the `+` operator does something entirely different when applied to floating-point values vs integers.
>
> Haskell's type classes specify a series of methods or values by their type signature, to be implemented by an instance declaration.

**Same function name, behavior depends on the type.**

![[Pasted image 20260223094655.png]]

![[Pasted image 20260223094732.png]]

---

## Coercion Polymorphism

Occurs when a language automatically converts one type to another — e.g., `float` to `int`.

---

## Related

- [[Stack Machines]]
