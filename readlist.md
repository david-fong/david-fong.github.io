
## General

- [Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Unicode Tools](https://unicode-table.com/en/tools/)
- [Why Isn't Functional Programming the Norm? - Richard Feldman](https://www.youtube.com/watch?v=QyJZzq0v7Z4&ab_channel=Metosin). More like: What makes a programming language become popular? Read some of the comments for a balance of viewpoint.
- [zkat](https://github.com/zkat/ama/issues/8)
- [The Myth of the Genius Programmer](https://www.youtube.com/watch?v=0SARbwvhupQ)
  - When is a good time to collaborate? `t=30m10s`
- [Apps or Web for Mobile](https://www.youtube.com/watch?v=4f2Zky_YyyQ)
  - From 2011, but arguments on each side are still very relevant.
- [Interview with Jeff Delaney](https://medium.com/illumination-curated/interview-with-jeff-delaney-from-youtubes-500k-fireship-channel-for-programmers-7d0d57eb8a1)
- monkeyuser.com

## Bash

- https://adambrodziak.medium.com/wasted-10-years-with-bash-a7f6cb480419

## GIT

### Shallow

1st lesson learned: don't clone forks. Do git init, then config remote refspec and alias shallow fetch, _then_ fetch from remote.

- [How to Update a Shallow Clone - Torek](https://stackoverflow.com/questions/41075972/how-to-update-a-git-shallow-clone)
- In summary:
  - Make a fork, delete stale branches in github, clone it with `--depth=100`
  - Add a remote upstream and edit .git/config refspec to only fetch important branches
  - `git config git config remote.upstream.tagopt --no-tags`
  - Run git fetch --all --depth=100

- [prune-packed](https://git-scm.com/docs/git-prune-packed)
- [refspec](https://git-scm.com/book/en/v2/Git-Internals-The-Refspec)
- [various prunes](https://stackoverflow.com/questions/20106712/what-are-the-differences-between-git-remote-prune-git-prune-git-fetch-prune)
  - [prune after change refspec](https://stackoverflow.com/questions/35937839/prune-remote-branches-after-fetch-refspec-changes)
  - [aggressive pruning](https://stackoverflow.com/questions/1904860/how-to-remove-unreferenced-blobs-from-my-git-repo)

```sh
# to convert to shallow after cloning deep:
git reflog expire --expire=all --all
git tag -d $(git tag -l)
git fetch --all --prune --depth=1
git gc --prune=all
```

## Microsoft Windows

- [Program Files x86](https://www.howtogeek.com/129178/why-does-64-bit-windows-need-a-separate-program-files-x86-folder/)

## The Web

### Unsorted

- [Imagine A Web Without Servers](https://www.youtube.com/watch?v=rJ_WvfF3FN8&ab_channel=JSConf)

### Standards

- [HTML's Design Principles - w3c](https://www.w3.org/TR/html-design-principles/)
  - [Interview with Ian Hickson](https://www.webstandards.org/2009/05/13/interview-with-ian-hickson-editor-of-the-html-5-specification/index.html)

### Security

- [The "Clear-Site-Data" header](https://www.w3.org/TR/clear-site-data/)
- ["Third Party CSS is Not Safe - Jake Archibald"](https://jakearchibald.com/2018/third-party-css-is-not-safe/)
- ["How to Stop Me Harvesting... - David Gilbertson"](https://medium.com/hackernoon/part-2-how-to-stop-me-harvesting-credit-card-numbers-and-passwords-from-your-site-844f739659b9)
- [About `rel=noopener` - Mathias Bynens](https://mathiasbynens.github.io/rel-noopener/)
  - Note that noreferrer implies noopener.
  - [better default becoming standardized](https://github.com/whatwg/html/pull/4330)
    - [whatg issue thread](https://github.com/whatwg/html/issues/4078)
    - [Chrome is still working on it](https://bugs.chromium.org/p/chromium/issues/detail?id=898942)
- [Security FAQ About Service Workers - Google](https://chromium.googlesource.com/chromium/src/+/master/docs/security/service-worker-security-faq.md)

- [link rel=nofollow](https://en.wikipedia.org/wiki/Nofollow)
- [The Most Annoying Site](https://www.youtube.com/watch?v=QFZ-pwErSl4&ab_channel=JSConf)

#### Vulnerability Feeds

- [NodeJS](https://nodejs.org/en/security/)
  - [RSS Feed](https://nodejs.org/en/feed/vulnerability.xml)
- [NPM](https://www.npmjs.com/advisories)
- [ExpressJS](https://expressjs.com/en/advanced/security-updates.html)
- [Death to IE11.com](https://death-to-ie11.com/)

### ARIA

```text
https://developer.mozilla.org/en-US/docs/Web/Accessibility/Keyboard-navigable_JavaScript_widgets
https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles
https://a11yproject.com/checklist/
https://a11y.coffee/
```

## Licensing

```text
https://creativecommons.org/faq/#can-i-apply-a-creative-commons-license-to-software
https://www.gnu.org/licenses/copyleft.html
https://opensource.org/licenses
```

### Non-Commercial Software Licences

Note that such a restriction by definition makes the licence non-open-source.

- [Commons Clause](https://commonsclause.com)
  - [notes](https://www.finnegan.com/en/insights/articles/why-open-source-licenses-with-a-commons-clause-may-become-less-common.html#:~:text=The%20Commons%20Clause%20is%20a,was%20publicly%20contributed%20by%20FOSSA.)
- [Prosperity Licence](https://prosperitylicense.com/)
- [PolyForm - NonCommercial](https://polyformproject.org/licenses/noncommercial/1.0.0/)

## JavaScript

### Lang Core

- [ES6 Classes - Anurag](https://medium.com/beginners-guide-to-mobile-web-development/super-and-extends-in-javascript-es6-understanding-the-tough-parts-6120372d3420)
- [prototypes - Rupesh Mishra](https://medium.com/better-programming/prototypes-in-javascript-5bba2990e04b)
- [Class Inheritance - javascript.info](https://javascript.info/class-inheritance)
- [The Mixin Pattern](https://javascript.info/mixins)
- [private fields in frozen object](https://github.com/tc39/proposal-private-fields/issues/69#issuecomment-636325319)

### Lang Quirks

- [`variable === undefined` vs `typeof variable === "undefined"`](https://stackoverflow.com/questions/4725603/variable-undefined-vs-typeof-variable-undefined)
- [Primitive Coercion - javascript.info](https://javascript.info/object-toprimitive)

### Package Management

- [pnpm](https://pnpm.js.org/en/motivation)
- [Yarn Plug'n'Play](https://yarnpkg.com/features/pnp)
- [Various JS Package Managers](https://medium.com/@Andrew_Mc/yarn-pnp-npm-tink-and-pnpm-oh-my-720d02221b4b)

### Module Systems

```text
https://stackoverflow.com/questions/45854169/how-can-i-use-an-es6-import-in-node
https://medium.com/@iamstan/typescript-es-modules-micheal-jackson-2040216be793
https://nodejs.org/api/esm.html#esm_enabling
```

### Browser Core

- [Event Ordering - quirksmode.org](https://www.quirksmode.org/js/events_order.html#link4)
- [Keyboard](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
  - [keycode.io](https://keycode.info/)
- [History Back-Foward Cache - web.dev](https://web.dev/bfcache/#always-close-open-connections-before-the-user-navigates-away)

#### Web Audio

```text
https://devdocs.io/dom/web_audio_api/best_practices
https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API
https://www.html5rocks.com/en/tutorials/webaudio/positional_audio/
https://github.com/GoogleChromeLabs/web-audio-samples/
https://github.com/bbc/r-audio
```

## CSS

- [CSS selector performance - csswizardry](https://csswizardry.com/2011/09/writing-efficient-css-selectors/)
- [Rachel Andrews](https://rachelandrew.co.uk/css/)

### Things I'm Waiting For / Excited About

- `sub-grid`
- `user-select: contain`
- `inset`

```text
https://medium.com/seek-blog/the-end-of-global-css-90d2a4a06284
https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties
https://developer.mozilla.org/en-US/docs/Web/CSS/display
flex playground: https://codepen.io/enxaneta/full/adLPwv/
https://github.com/fergald/docs/blob/master/explainers/css-shadow-parts-1.md
https://developers.google.com/web/updates/2019/02/constructable-stylesheets
https://devdocs.io/css/clip-path
https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders
https://developers.google.com/web/updates/2018/01/paintapi
https://drafts.csswg.org/mediaqueries-5/#custom-mq
styling east-asian fonts: https://developer.mozilla.org/en-US/docs/Web/CSS/font-variant-east-asian
```

## SVG

- [cool water with filters](https://codepen.io/soju22/pen/OqPyrm)
- [filter playground](https://yoksel.github.io/svg-filters/#/)

## C++

- [`<windows.h>`](https://docs.microsoft.com/en-us/windows/console/console-virtual-terminal-sequences#EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING)

## Rust

- [](https://www.reddit.com/r/cpp/comments/611811/have_you_used_rust_do_you_prefer_it_over_modern_c/)
- [Fire Flowers](https://brson.github.io/fireflowers/)


