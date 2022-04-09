
## display none

Out of layout.
Children cannot make themselves visible.
No pointer events. No tab navigation.
No ctrl+f within.
Destroys rendering state.

## content-visibility hidden

Out of layout.
Children cannot make themselves visible.
No pointer events. No tab navigation.
No ctrl+f within.
Saves snapshot of rendering state, but does not continue update it.

Turns on containment of layout, paint, and style, which also creates a new containing block, a new stacking context, and a new block-formatting context.

## visibility hidden

Still affects layout.
Inherited. Children can make themselves visible.
No pointer events. No tab navigation.
Cannot receive keyboard events.
No ctrl+f within.
Continues updating rendering state.

## opacity 0

Still affects layout.
Children can only further decrease their opacity- not restore.
Has pointer events and tab navigation.
ctrl+f still works within.

using a value other than one creates a new stacking context.

## HTML inert attribute

**Still visible.**
No tab navigation within, no pointer events, no ctrl+f within.
Not widely implemented yet (as of early 2021).

