---
layout: post
title: Vue Uncategorized rules to have a better life
# teaser: "Some useful Uncategorized Vue rules that will make your daily life a little easier."
teaser: "The Vue ESLint plugin has several rules that are uncategorized and it turns out many will make your daily life a little easier."
authors:
  - BobToninho
categories:
  - Case Studies
tags:
  - Guest Post
  - Rules
---

<!--Why would ESLint users want to read this? What benefit are they receiving? Why would they read this instead of something else?-->
<!--Same for Vue users?-->
<!--What are the benefits you’ve seen, not just “it makes code the way I like it,” but practically speaking? Did you reduce bugs? Did it help in another way?-->
<!--What is the conclusion you’d like readers to take away?-->

<!--The [esling-plugin-vue](https://eslint.vuejs.org/) plugin divides its rules in the following categories:-->
The official Vue ESLint plugin, [eslint-plugin-vue](https://eslint.vuejs.org/), groups its rules into the following categories:

- Base
- Essential
- Strongly recommended
- Recommended
- Uncategorized
- Extensions

<!--I spent some time digging into the *uncategorized* category to see what can be useful to help avoid distractions in commits and, of course, to enforce the same style in all parts of a Vue project. In my opinion, all Vue projects should use the Recommended category, which enforces a lot (if not all) of the topics mentioned in the [style guide](https://vuejs.org/style-guide/).-->
I spent some time digging into the uncategorized category to see which rules might be useful to help avoid problems in commits and to enforce the same style in all parts of a Vue project. In my opinion, all Vue projects should use the Recommended category, which enforces a lot (if not all) of the topics mentioned in the [style guide](https://vuejs.org/style-guide/).

### `vue/component-name-in-template-casing`

I like to keep the rule this way:

```json
{
  "vue/component-name-in-template-casing": ["error", "PascalCase"]
}
```

The PascalCase convention for component names helps distinguish more clearly a component from an actual HTML element. Additionally, depending on the theme, your editor or IDE will highlight a component in PascalCase with a different color with respect to an actual HTML element. In my experience, I find this small tweak especially useful when managing big components.

### `vue/match-component-file-name`

This rule tells you when your component `name` property is different from its file name (but the same name in kebab-case and PascalCase is allowed, e.g. `app-carousel` and `AppCarousel` are considered the same).

For this rule to work with the majority of Vue projects, we need to slightly change the default value, which only checks for `.jsx` extensions.

```json
{
  "vue/match-component-file-name": ["error", {
    "extensions": ["vue"]
  }]
}
```

This is really just a better life rule. When using it, the component name and the file name will become a single thing, freeing that couple of bytes of RAM in your brain allocated to match the component name with the file name.

### `vue/no-unused-properties`

This rule tells you when a component has some properties that are not used anywhere in `<template>` or the `<script>` part.

When using this rule, I soften its effect to a `warn`, because I don't want it to yell at me when quickly prototyping a component or while creating a new one.

```json
{
  "vue/no-unused-properties": "warn"
}
```

<!--Possible more content: In order to no pollute commits you can use...-->
<!--vue/html-comment-content-spacing-->
<!--vue/no-empty-component-block-->
