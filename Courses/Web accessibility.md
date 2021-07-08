# Web accessibility

Course repo: https://github.com/udacity/ud891

Alice Boxhall, software engineer at Accessibility team, Google
Rob Dodson, developer advocate for Chrome, Google

"Accessibility is a pain to spell"

Victor Tsaran

A concussion can impair a person's visual, cognitive, and motor abilities.

WCAG principles: perceivable, operable, understandable, robust (POUR)
📖 WCAG checklist: https://webaim.org/standards/wcag/checklist

Braille keyboard for Android: https://en.swiftbraille.com/

## Focus

Tab / Shift+Tab. Tab order.

Some elements are implicitly focusable: input, button, select. Others are not (e.g. headings)

DOM order matters: check tab order frequently to make sure you didn't mess it up

- tabindex="-1": not in natural tab order, can be programmatically focused with focus() (e.g. ```document.querySelector('#modal').focus()```). Useful for modals.
- tabindex="0": in natural tab order (even if it isn't implicitly focusable!), can be programmatically focused
- tabindex="5": in natural tab order, jumped to the front of tab order, anti-pattern!!!! Move up in the dom instead.

Only add focus to elements that require input, interaction, NOT to content.

Managing focus: e.g. internal links, single page applications. Add tabindex="-1" to headers, use focus() method.

[Skip links](http://webaim.org/techniques/skipnav/)

[ARIA design pattern stock](https://www.w3.org/TR/wai-aria-practices-1.1/#radiobutton)

Roving focus: use tabindex="0" checked, tabindex="-1"

document.activeElement in console returns the element that is currently active, even if it's hidden

Keyboard trap: focus is never locked. BUT on modals it can be useful: e.g. 'open'.