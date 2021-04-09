
# OOP Programming Language Ideas

Much of this has to do with syntax rather than language capability.

It's also not an attempt to create something completely new. I just want to change some things that bug me about common OOP languages.

## Things I don't like

### Syntax

- I want it to be explicit when I reference a member of `this` and `super`, but I also want it to be as terse as possible.
- I want member access modifiers to be tied to the variable name.
- I don't like the exclamation mark to toggle true/false. It's hard to see and it doesn't read like english.

### Feature Cherry-Picking

- I like when method signatures can restrict mutation of the object.
  - This makes it easy to pass an object somewhere as a readonly view.
- I like when variables can't be reassigned by default.

### IDE Things

- I don't like how strings and multiline comments wonked up the syntax-highlighting when the closing delimiter gets temporarily deleted.

---

## Proposed Solutions

- No implicit `this` within a class context.
  - Instead of `this.<member>`, `.<member>`.
  - Instead of `super.<member>`, `..<member>`.
- Member access modifiers specified by naming.
  - Double underscore prefix means private.
  - Single underscore prefix means protected.
- `ro` means "readonly".
- switch statements do not fallthrough by default.
- string literals are specified with `"( )`.
  - all lines following the first line in a multiline string will ignore all leading whitespace up to and including a mandatory `|` character.
- for loops need to enable break, continue, and return to use inside.

- Access modifiers for fields that are collections:
  - Able to specify public-readonly: only modifiable internally

## "Wave" Idea

I'm trying to come up with a super terse way to communicate access modifiers and nullability, which also enables controlling access for contents of fields that are collections.

- Use the `_.=?` as access modifiers.
- `_` means hidden, `.` means read-only, `=` means read and write. `?` means nullable.
- When used on fields, the modifiers are in a tuple of public-protected-private. For any examples below, a question mark can be appended to indicate nullability.
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
  - When the field is an array, you can control the access modifiers for the contents:
    - Below are some sensible usages:
      - `... f0 [..=] number`
      - `... f0 [.==] number`
    - Here's how nesting works:
      - `... f0 [.==][...] number`
      - `..= f0 [..=][===?][.==] number`
      - `...? f0 [.==?][.==][...?] number`
    - When the field is hiden from public and protected, up to that part of the array access tuple is omitted:
      - `_.. f0 [.=] number`
      - `__. f0 [=] number`
      - `... f0 [.==][_..][.=][_.][=] number`
- When used on methods, 

I thought about making it mandatory to prepend `@` on the name of a member that is an accessor property, because I thought it would be nice for it to be visibly obvious, but I dont' like that this would break libraries if a property is changed between plain data and accessor type. I think this is better left to an editor program to do something like italicize the font.

I haven't thought of what to do about the `static` keyword. Maybe something similar to JavaScript "classes" where the constructor and prototype are clearly separate.

## Terminology Ideas

I'm not a big fan of the OOP terminology that has been popularized by Java. Here are some of my ideas on what I might prefer. I'm trying to reduce the amount of terminology and name things after what they do.

- abstract -> incomplete
- override -> re-implement
- interface -> description

