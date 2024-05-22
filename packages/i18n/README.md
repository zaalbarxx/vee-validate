# @zaalbarxx/vee-validate-i18n

<p align="center">
  <a href="https://vee-validate.logaretm.com/v4/guide/i18n" target="_blank">
    <img width="150" src="https://github.com/logaretm/vee-validate/blob/main/logo.png">
  </a>
</p>

> Localization module for vee-validate

## What's this

VeeValidate v4 breaks up the parts that made it a popular solution for form validation into it isolated parts. The core `vee-validate` package no longer includes logic for localization.

This is where this package comes in.

## Installation

```sh
yarn add @zaalbarxx/vee-validate-i18n

# or with npm
npm install @zaalbarxx/vee-validate-i18n
```

## Usage

import the `localize()` function from `@zaalbarxx/vee-validate-i18n` which returns a message generator function:

```js
import { defineRule, configure } from '@zaalbarxx/vee-validate';
import { required } from '@zaalbarxx/vee-validate-rules';
import { localize } from '@zaalbarxx/vee-validate-i18n';

// Define the rule globally
defineRule('required', required);

configure({
  // Generates an English message locale generator
  generateMessage: localize('en', {
    messages: {
      required: 'This field is required',
    },
  }),
});
```

If you have multiple locales in your application, you can add them like this:

```js
import { defineRule, configure } from '@zaalbarxx/vee-validate';
import { required } from '@zaalbarxx/vee-validate-rules';
import { localize } from '@zaalbarxx/vee-validate-i18n';

// Define the rule globally
defineRule('required', required);

configure({
  generateMessage: localize({
    en: {
      messages: {
        required: 'This field is required',
      },
    },
    ar: {
      messages: {
        required: 'هذا الحقل مطلوب',
      },
    },
  }),
});
```

You can change the locale using `setLocale` function exported by the `@zaalbarxx/vee-validate-i18n` anywhere in your application:

```js
import { setLocale } from '@zaalbarxx/vee-validate-i18n';

setLocale('ar');
```

## Available Languages

To save you a lot of time translating `@zaalbarxx/vee-validate-rules` messages to your language, the awesome community around vee-validate already contributed over **40+ languages** that you can use directly in your application and get started quickly. The localized files include localized messages for all the global rules provided by `@zaalbarxx/vee-validate-rules` package.

You can import the locales from their JSON directory like this:

```js
import { configure } from '@zaalbarxx/vee-validate';
import { localize } from '@zaalbarxx/vee-validate-i18n';
import en from '@zaalbarxx/vee-validate-i18n/dist/locale/en.json';
import ar from '@zaalbarxx/vee-validate-i18n/dist/locale/ar.json';

configure({
  generateMessage: localize({
    en,
    ar,
  }),
});
```

You can view a list of the available languages by [checking the locale folder](https://github.com/logaretm/vee-validate/tree/main/packages/i18n/src/locale)
