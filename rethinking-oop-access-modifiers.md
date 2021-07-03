
# Terse, Expressive OOP Access Modifiers

## Motivation

Here are things I don't really like about access modifiers in popular OOP languages:

- The keywords are verbose.

- The word "protected" is confusing.

- The C++ label style seems like a bandaid solution to verbosity. It creates another problem: I can't tell what a field's access is just by looking at the line it's on.

- In Java, often I need to make getters and setters just to enforce different read/write permissions at different access levels.

## Proposal

- Use the `?` character as a nullability modifier. It prepends the types specifier

- Use the `_.=` characters as access modifiers.
  - `_` means hidden, `.` means read-only, `=` means read and write.
  - I think these characters leverage already-common ideas: underscore is typically used to represent hidden-ness. The dot is used for property access (reading), and the equal sign is used for setting values (writing).

### Contextual Meanings

- When prepending fields, the modifiers are a tuple of {public, protected, private} (I haven't decided on whether to include one for internal). read-write specifies whether the variable can be _reassigned_ (mutability is a separate matter).

- When prepending class type specifiers, it is a tuple of object mutability {public, protected, private}.
  - Here the `_` character has no practical usage, so it can't be used, and if the value is not accessible at a certain level, the read-write character for that level should be omitted.
  - If `.` is used, that means that at that visibility level, no fields of the object can be reassigned or mutated, and no non-const methods can be called.

- When prepending globals, they are a tuple of {package-exported, package-internal, file-interal}.

The full tuples must be specified. There is no defaulting because I don't believe there is a hands-down, objectively, pragmatically good default to infer. Java defaults to package-private. Rust defaults to private. C++ has class and struct. TypeScript defaults to public. There's no language-agnostic consensus. Besides, the tuples are _three characters wide_. I don't see a terser, simpler, and more expressive way to do the same thing, _and_, making the whole uple required will enforce some column-wise alignment of field declarations, which always makes me happy. Perhaps it's silly, but that's one of the things that bothers me about the whole private / protected / internal / public business.

### Examples for Field Visibility

- Below are all the sensible combinations:
  - `__.` Java private final.
  - `__=` Java private.
  - `_..` Java protected final.
  - `_.=` Java private with protected getter.
  - `_==` Java protected.
  - `...` Java public final.
  - `..=` Java private with public getter.
  - `.==` Java protected with public getter.
  - `===` Java public.
  - Other combinations are technically fine, but they don't have much use-case or parallels in common languages.

### Integration with Collection Types

- When the field is a collection such as an array, you can control the access modifiers for the contents:
  - Below are some sensible usages:
    - `... f0 [..=] ===number`
    - `... f0 [.==] ..=number`
  - Here's how nesting works:
    - `... f0 [.==] [...] ..=number`
    - `..= f0 [..=] [===] ?[.==] ...number`
    - `... f0 ?[.==] [.==] [...] ?.==number`
  - When the field is hiden from public and protected, up to that part of the array access tuple is omitted:
    - `_.. f0 [.=] ..number`
    - `__. f0 [=] .=number`
    - `... f0 [.==][_..][.=][_.][=] =number`

I thought about making it mandatory to prepend `@` on the name of a member that is an accessor property, because I thought it would be nice for it to be visibly obvious, but I dont' like that this would break code that consumes a library if that library changes a property between plain data and accessor type. I think this is better left to an editor program to do something like italicize the font.

I haven't thought of what to do about the `static` keyword. Maybe something similar to JavaScript "classes" where the constructor and prototype are clearly separate.

I haven't thought about how this syntax could possibly used to improve method access and overriding permissions, but I intend to try. It certainly should not be usable on the array-entry-access operator or the iterator operator, since that should be left for the instance declaration variable to decide.
