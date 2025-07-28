# Testplane testing library

## Introduction
[Testing-library](https://testing-library.com/) is a collection of tools for testing web application user interfaces, focused on creating reliable and maintainable tests by emphasizing user behavior. The main advantage of `testing-library` is its focus on interaction with interface elements. And in testplane, you can use the element search methods provided by the `testing-library` itself.

## Connection

1. Install the npm package `@testplane/testing-library`
```shell
npm i -D @testplane/testing-library
```

2. Include it in the Testplane config in the `prepareBrowser` section:
```js
// .testplane.conf.js
const { setupBrowser } = require("@testplane/testing-library");

module.exports = {
    prepareBrowser(browser) {
        setupBrowser(browser);
    },

    // other Testplane settings...
};
```

## Usage

After configuring, you will be able to use the search by selectors from `testing-library`, as described in the [official documentation](https://testing-library.com/docs/queries/about/). For example, searching for an element by its text:

```js
it("example", async ({ browser }) => {
    await browser.url("https://github.com/");

    const newRepoButton = await browser.getByText("New");

    await newRepoButton.click();
});


```

This feature will also be available in the context of found elements:

```js
it("example", async ({ browser }) => {
    await browser.url("https://github.com/");

    const sidebar = await browser.$(".dashboard-sidebar");
    const newRepoButton = await sidebar.getByText("New");

    await newRepoButton.click();
});
```
