---
aliases:
  - Types Deep Dive
  - Polymorphism Deep Dive
tags:
  - school
  - school/cs381
---
# Types and Polymorphism — Deep Dive

Companion to [[Types and Polymorphism]] — Part of [[CS381 - Notes]]

---

## Static vs Dynamic — What They Actually Mean

**Static typing** = types are checked at *compile time*. The compiler knows the type of every expression before the program runs.

**Dynamic typing** = types are attached to *values* at *runtime*. The interpreter checks types as the program executes.

**Languages by typing:**

| Language | Typing |
|----------|--------|
| Haskell, Java, C, C++, Rust, Go | Static |
| Python, JavaScript, Ruby, Lisp | Dynamic |
| TypeScript | Static (compiled from JS) |

**The tradeoffs honestly:**

| | Static | Dynamic |
|--|--------|---------|
| Catches type errors | At compile time — before you run | At runtime — when it crashes |
| Flexibility | Less — compiler rejects uncertain programs | More — anything goes until it breaks |
| Performance | Generally faster (compiler can optimize) | Generally slower (type checks at runtime) |
| Prototyping speed | Slower (must satisfy type checker) | Faster (just run it) |
| IDE support | Excellent (types tell IDE everything) | Limited |

---

## Why Static Typing Rejects Valid Programs

This is the undecidability point from your notes. A simple example:

```python
if False:
    x = 1 + "hello"   # type error — but this line NEVER runs
```

A static type checker sees `1 + "hello"` and rejects it — even though `False` means this branch is dead code that will never execute. The checker can't always know which branches run (that would require evaluating the program).

Haskell's rule: **if we can't prove it's type-correct, we reject it.** This means some valid programs get rejected. That's the price of static safety.

---

## The Four Types of Polymorphism — Cleaner Examples

### 1. Subtype Polymorphism (Inheritance / Runtime)

**One interface, multiple implementations chosen at runtime.**

```cpp
class Animal {
public:
    virtual void speak() = 0;  // pure virtual — must be overridden
};

class Dog : public Animal {
public:
    void speak() { cout << "Woof" << endl; }
};

class Cat : public Animal {
public:
    void speak() { cout << "Meow" << endl; }
};

Animal* a = new Dog();
a->speak();   // prints "Woof" — decided at RUNTIME (dynamic dispatch)
```

The variable `a` has type `Animal*`, but the *behavior* comes from `Dog`. The correct `speak` is chosen at runtime based on the actual object. This is **dynamic dispatch**.

**Key:** same interface (`Animal`), different behavior per type, resolved at **runtime**.

---

### 2. Parametric Polymorphism (Generics / Compile-time)

**Same code, same behavior, works for any type.**

```haskell
-- Works for a list of ANYTHING
length :: [a] -> Int
length []     = 0
length (_:xs) = 1 + length xs

-- Works for any comparable type
maximum :: Ord a => [a] -> a
maximum [x]    = x
maximum (x:xs) = max x (maximum xs)
```

```cpp
// C++ templates — same idea
template<typename T>
T maximum(T a, T b) { return a > b ? a : b; }

maximum(3, 5);       // works for int
maximum(3.0, 5.0);   // works for double
maximum('a', 'z');   // works for char
```

**Key:** same code, same behavior, resolved at **compile time**. The compiler generates separate versions per type (in C++) or uses type erasure (in Java).

---

### 3. Ad-Hoc Polymorphism (Type Classes / Overloading)

**Same function name, different behavior per type.**

```haskell
-- The Show type class — anything that can be converted to String
class Show a where
    show :: a -> String

-- Int's implementation
instance Show Int where
    show n = -- Int-specific formatting

-- Bool's implementation
instance Show Bool where
    show True  = "True"
    show False = "False"

-- Usage:
show 42      -- "42"   (uses Int's Show)
show True    -- "True" (uses Bool's Show)
```

In C++, this is **function overloading**:
```cpp
void print(int x)    { cout << x; }
void print(double x) { cout << x; }
void print(string x) { cout << x; }

print(42);      // calls the int version
print(3.14);    // calls the double version
```

**Key:** same function name, *different* behavior per type. Which version runs depends on the type.

---

### 4. Coercion Polymorphism (Implicit Conversion)

**The language automatically converts one type to another.**

```c
int x = 5;
double y = x + 1.5;   // x is automatically converted to double
// y = 6.5
```

```python
x = 5
y = x + 1.5   # Python promotes x to float automatically
```

Coercion is distinct from the others — it's not about *defining* behavior for multiple types, it's about *converting* between types transparently.

**Explicit casting vs implicit coercion:**
```c
double d = 9.7;
int i = (int) d;      // explicit cast — you asked for it (i = 9)
int j = d;            // implicit coercion — compiler does it (also j = 9, with a warning)
```

---

## The `<T>` vs `virtual` Confusion

The slide in your notes mixed these up. They are fundamentally different:

| | `<T>` (generics/templates) | `virtual` |
|--|---------------------------|-----------|
| Type | Parametric polymorphism | Subtype polymorphism |
| Resolved | Compile time | Runtime |
| Mechanism | Type parameters | Dynamic dispatch via vtable |
| Same behavior? | Yes — same code runs | No — different implementations per type |

```cpp
// <T> — parametric, compile time, SAME behavior
template<typename T>
T identity(T x) { return x; }

// virtual — subtype, runtime, DIFFERENT behavior
class Base { virtual void doThing() { print("Base"); } };
class Derived : Base { void doThing() { print("Derived"); } };
```

---

## Haskell Type Inference

Haskell can infer types without you writing them. This uses the **Hindley-Milner** type inference algorithm.

```haskell
-- You write:
add x y = x + y

-- Haskell infers:
add :: Num a => a -> a -> a
-- (works for any numeric type)
```

This is why Haskell type signatures are optional — the compiler figures it out. But writing them is good practice and helps with error messages.

---

## Things to Know for Exams

- Static = compile time. Dynamic = runtime.
- Static rejects some valid programs — this is undecidability, not a bug.
- **Subtype**: `virtual`, runtime, different behavior, same interface
- **Parametric**: `<T>` or `[a]`, compile time, same behavior, any type
- **Ad-hoc**: type classes / overloading, same name, different behavior per type
- **Coercion**: automatic type conversion (implicit = coercion, explicit = cast)
- `show` in Haskell is an example of ad-hoc polymorphism (type class)
- The `+` operator is ad-hoc — does different things for Int vs Float

---

## Related

- [[Types and Polymorphism]]
- [[CS381 - Notes]]
- [[Stack Machines]]
