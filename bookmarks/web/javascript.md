# JavaScript

- [Good comment on cases in which one should have progressive enhancement for when javascript is not there](https://www.reddit.com/r/webdev/comments/48z7jz/do_you_take_into_account_those_who_disable/d0nxftd/)

## Lang Core

- [ES6 Classes - Anurag](https://medium.com/beginners-guide-to-mobile-web-development/super-and-extends-in-javascript-es6-understanding-the-tough-parts-6120372d3420)
- [prototypes - Rupesh Mishra](https://medium.com/better-programming/prototypes-in-javascript-5bba2990e04b)
- [Class Inheritance - javascript.info](https://javascript.info/class-inheritance)
- [The Mixin Pattern](https://javascript.info/mixins)
- [private fields in frozen object](https://github.com/tc39/proposal-private-fields/issues/69#issuecomment-636325319)

## Lang Quirks

- [`variable === undefined` vs `typeof variable === "undefined"`](https://stackoverflow.com/questions/4725603/variable-undefined-vs-typeof-variable-undefined)
- [Primitive Coercion - javascript.info](https://javascript.info/object-toprimitive)
- [string encodings](https://kevin.burke.dev/kevin/node-js-string-encoding/)
  - [more](https://dmitripavlutin.com/what-every-javascript-developer-should-know-about-unicode/)

## Package Management

- [pnpm](https://pnpm.js.org/en/motivation)
- [Yarn Plug'n'Play](https://yarnpkg.com/features/pnp)
- [Various JS Package Managers](https://medium.com/@Andrew_Mc/yarn-pnp-npm-tink-and-pnpm-oh-my-720d02221b4b)

## Module Systems

```text
https://stackoverflow.com/questions/45854169/how-can-i-use-an-es6-import-in-node
https://medium.com/@iamstan/typescript-es-modules-micheal-jackson-2040216be793
https://nodejs.org/api/esm.html#esm_enabling
```

- [](https://blog.sindresorhus.com/get-ready-for-esm-aa53530b3f77)

## Engine Things & Tricks

https://mrale.ph/blog/2015/01/11/whats-up-with-monomorphism.html


```javascript
// fast large-json-serializable-object initialization
// https://v8.dev/blog/cost-of-javascript-2019#json
`JSON.parse('${jsonStr.replace(/[\\']/g, "\\$&")}')`
```

## Browser Core

- [Event Ordering - quirksmode.org](https://www.quirksmode.org/js/events_order.html#link4)
- [Keyboard](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
  - [keycode.io](https://keycode.info/)
- [History Back-Foward Cache - web.dev](https://web.dev/bfcache/#always-close-open-connections-before-the-user-navigates-away)

### Web Audio

```text
https://devdocs.io/dom/web_audio_api/best_practices
https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API
https://www.html5rocks.com/en/tutorials/webaudio/positional_audio/
https://github.com/GoogleChromeLabs/web-audio-samples/
https://github.com/bbc/r-audio
```