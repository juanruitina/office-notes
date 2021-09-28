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

==Only add focus to elements that require input, interaction, NOT to content.==

Managing focus: e.g. internal links, single page applications. Add tabindex="-1" to headers, use focus() method.

[Skip links](http://webaim.org/techniques/skipnav/)

[ARIA design pattern stock](https://www.w3.org/TR/wai-aria-practices-1.1/#radiobutton)

Roving focus: use tabindex="0" checked, tabindex="-1"

document.activeElement in console returns the element that is currently active, even if it's hidden

Keyboard trap: focus is never locked. BUT on modals it can be useful: e.g. 'open'.

## Semantics

Interacting with web with screen reader, braille display, magnification, voice control, switch access, sip and puff, eye tracking -> depends on programmatically expressed semantics

Affordances: e.g. handle of a kettle is self-explanatory, gives visual clue.

Web AIM WCAG 2.0 Checklist 4.1.2: Name, Role, Value

Voice control and switch control use the same programmatically controlled semantics as screen readers.

If tagged right, we can expect elements' role, name, state and value

Label and name mean the same.

- Visible label: e.g. checkbox label
- Text alternative: e.g. image alt text

- Form inputs have associated labels (wrap in label or use for+id attribute) -> results in toggling checkbox when clicking on label

## Navigating content

Page summary on Voice Over gives information like number of headings, landmarks, forms.

Web rotor helps navigate headings: Ctrl+Option+U

Shortcuts mentioned:

- CMD+F5 to turn on VoiceOver on OS X
- Normal keyboard operation (TAB, Shift+TAB, arrow keys etc.) work as normal with VoiceOver running
- CMD+L to jump to address bar
- CTRL+Option+U to open Web Rotor
- Type search term with Web Rotor open to search within Web Rotor
- CTRL + Option + ← ↑ ↓ → to explore content
- CTRL + Option + CMD + H to move forward by heading
- CTRL + Option + CMD + Shift + H to move backward by heading

WebAIM's article on Using VoiceOver to evaluate Web Accessibility has a full introduction to VoiceOver from the point of view of evaluating accessibility, including most keyboard commands available.

If you don't have a Mac device, NVDA is a free, open source screen reader available for Windows. WebAIM's introduction to NVDA covers the basics of using NVDA to check accessibility.

If you only use Linux, Orca is available in the Gnome desktop manager, although this screen reader is much more rarely used and suffers from poor support by web browsers.

1.3.2 Meaningful sequence

WebAIM checklist items:

- 1.3.2: http://webaim.org/standards/wcag/checklist#sc1.3.2
- 2.4.10: http://webaim.org/standards/wcag/checklist#sc2.4.10
- 1.3.1: http://webaim.org/standards/wcag/checklist#sc1.3.1
- 2.4.1: http://webaim.org/standards/wcag/checklist#sc2.4.1
- 2.4.6: http://webaim.org/standards/wcag/checklist#sc2.4.6

JavaScript headings snippet:

```javascript
for (var i = 0, headings = $$('h1,h2,h3,h4,h5,h6');
     i < headings.length; i++) {
   console.log(headings[i].textContent.trim() + " " +  
               headings[i].tagName,
               headings[i]);
}
```

Link antipatterns:

1. Span with link styling
2. Anchor tag without href attribute

Always use a link:

- Shows up in link list
- Works with keyboard
- Can be bookmarked

3. Button implemented as link
4. Image used as link content. Use alt text!

WebAIM checklist item 2.4.9: http://webaim.org/standards/wcag/checklist#sc2.4.9

Use heading inside section

Use nav for table of contents

## Semantics: ARIA
WAI-ARIA: Web Accessibility Initiative's Accessible Rich Internet Applications spec

ARIA attributes always need to have explicit values

? https://classroom.udacity.com/courses/ud891/lessons/8311490720/concepts/724c168a-37e0-43e5-9174-6170bf0cb4c9 Couldn't figure this out

### Roles

Shorthand for a particular UI pattern

- ARIA 1.0 roles: https://www.w3.org/TR/wai-aria-1.0/#roles
- ARIA 1.1 roles (draft): https://www.w3.org/TR/wai-aria-1.1/#roles
- ♥ ARIA 1.1 practices guide (draft): https://www.w3.org/TR/wai-aria-practices-1.1/

Check which states and properties are required for any given role

aria-owns: use to indicate a child that is separate from parent in the DOM. E.g. floating menus and submenus.

? `hidden` attribute?