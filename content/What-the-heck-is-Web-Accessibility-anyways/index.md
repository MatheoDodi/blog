---
title: "What the heck is Web Accessibility, anyways?"
description: "Types of disabilities : https://www.w3.org/WAI/people-use-web/abilities-barriers/"
date: "2019-05-31T21:49:10.414Z"
categories: []
published: false
---

  

Types of disabilities : [https://www.w3.org/WAI/people-use-web/abilities-barriers/](https://www.w3.org/WAI/people-use-web/abilities-barriers/)

How to browse the web : Keyboard, Screen Readers, Switches, Wands

#### Tabindexes 

The `**tabindex**` [global attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes) indicates if its element can be focused, and if/where it participates in sequential keyboard navigation (usually with the Tab key, hence the name). Tab takes you forward, Shift+Tab takes you back. Elementes that are tabable a, button, input, select, textarea, iframe. Presentational items are usually not tabable (divs, spans). All items can be made tabable though by the developers. HTML attribute tabindex makes any element tabable. They can take a negative value which means that it is focusable but only programmatically via JavaScript, it cannot be reached simply by tabbing. `tabindex="0"` allows elements besides links and form elements to receive keyboard focus. It does not change the tab order, but places the element in the logical navigation flow, as if it were a link on the page. `tabindex="1"` (or any number greater than 1) defines an explicit tab order. Not only the element is tabable, but now we’ve removed it from the normal flow of the tab navigation and defined it to be focused before any of the other elements. It should only be used in rare cases where we might want to give attention to something that’d be important to our users (and no, your Call-To-Action button that says”Buy Now” is not _that_ important to the user) and it’s definitely not the way to fix the flow of an unorganized navigation due to poorly written source code.

#### Visible Focus

help a person know which element has the keyboard focus. Never remove the focus outlineThis Success Criterion helps anyone who relies on the keyboard to operate the page, by letting them visually determine the component on which keyboard operations will interact at any point in time. People with attention limitations, short term memory limitations, or limitations in executive processes benefit by being able to discover where the focus is located.

### “Skip Navigation” Links

The main content is not usually the first thing on a web page. Keyboard and screen reader users generally must navigate a long list of navigation links, sub-lists of links, corporate icons, site searches, and other elements before ever arriving at the main content. This is particularly difficult for users with some forms of motor disabilities.

Without some sort of system for bypassing the long list of links, some users are at a huge disadvantage. Consider users with no arm movement, who use computers by tapping their heads on a switch or that use a stick in their mouth to press keyboard keys. Requiring users to perform any action perhaps 100s of times before reaching the main content is simply unacceptable.

Of course, sighted people who use their mouse do not have any trouble with pages such as this. They can almost immediately scan over the page and identify where the main content is. In effect, sighted users have a built-in “skip navigation” mechanism: their eyes. They can also bypass the many links before the main content and click directly on the link they want with the mouse. The “skip navigation” idea was invented to give screen reader and keyboard users the same capability of going directly to the main content that sighted mouse users take for granted.

The link is the first item in the page. The anchor or target for the link (where the link will jump the user to) is placed at the beginning of the main content.

`<body>  
<a href="#maincontent">Skip to main content</a>   
...  
**<main id="maincontent">**  
<h1>Heading</h1>  
<p>This is the first paragraph</p>`

The target is identified by its `id` attribute value matching the `href` value (minus the "#") of the "skip" link.

#### ALT Text

Usually the very first think that someone thinks of when the word _accessibility_ is mentioned, is alt text when it comes to images. Also good for SEO. How to write good alt text :

**Describe the image as specifically as possible.**

**Keep it (relatively) short.** Keep your alt text fewer than 125 characters.

**Don’t include “image of,” “picture of,” etc. in your alt text.** It’s already assumed your alt text is referring to an image, so there’s no need to specify it.

**Don’t forget longdesc=””.** Explore using the longdesc=”” tag for more complex images that require a longer description.

**Use your keywords, but sparingly.**

#### ALT Text Tips

If you’d like an image to be skipped for your screen reader users than you can provide an empty alt=”” tag, screen realize that it’s empty the image will be completely skipped without trying to read it’s filename.

If you capitalize all the alt text letters than screen readers will read that word letter by letter.

If you’d like to hide something from screen-readers you can use : display: none; visibility: hidden; <input hidden />

#### LABELS

When we first started learning HTML, we’re not really taught with accessibility in mind, and that results to some questions like _“well, why do I need a label tag for an input, anyways?”_, Placeholder looks much cooler and it even disappears as I’m writing. The problem though is, that some screen readers **do not** read placeholder text, so labels are very important for accessibility, because it help screen reader users know what the input that will follow, is about. You should always include a _for_ attribute that points to the id for the input element.

Right way to do it :   
<label for=”username”>Enter username</label>  
<input type=”text” id=”username” placeholder=”Enter username” />

#### Aria-labelledby

The `[aria-labelledby](https://www.w3.org/TR/wai-aria/#aria-labelledby "http://www.w3.org/TR/wai-aria/states_and_properties#aria-labelledby")` attribute establishes relationships between objects and their label(s), and its value should be one or more element IDs, which refer to elements that have the text needed for labeling. List multiple element IDs in a space delimited fashion.

Using this, you can kind of get away from using labels and the _for_, since with the aria-labelledby you can establish a relationship between any element although to improve compatibility with user agents that do not support ARIA, you can use `aria-labelledby` with the `[<label>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label "The HTML <label> element represents a caption for an item in a user interface.")` element (using the `for` attribute).

#### Roles

They are yet another way to make our content more accessible to users with disabilities and they can be added to an HTML element with role=”ROLE\_TYPE”. Before HTML5 brought us a lot of the semantic elements like “main”, “nav”, “article”, “footer” ARIA roles would be used on the elements to describe the…well, the _role_ of that element. If one takes a loot at the spec for ARIA roles they might feel a little intimidated due to the fact that there are a lot of ARIA roles and there’s certain things one has to keep in mind when using them, but this [Cheat Sheet](http://karlgroves-sandbox.com/CheatSheets/ARIA-Cheatsheet.html) does a great job listing out all of them as well as their analogous HTML element. Which brings me to my next point.

#### Semantic HTML

By far the easiest win when it comes to Web Accessibility, and maybe the most important one, is using semantic HTML. This means using the most descriptive and appropriate tag for your content

#### ARIA

Earlier, I mentioned the word _ARIA_ and you might be wondering what that is or what it means. Let me expand a little on this. ARIA stands for **A**ccessible **R**ich **I**nternet **A**pplications.

#### ARIA Live Regions

  

#### Color

NoCoffee chrome extension.