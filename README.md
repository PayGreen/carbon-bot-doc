PayGreen - CarbonBot - Widget JS
===========

## ClimateKit documentation
In order to understand how to create a carbon footprint and get your tokens, you can to check our ClimateKit API documentation: https://api-climatekit.paygreen.fr/documentation/climate


## 1. Adding JS script
Add the javascript file in your code:
```html
<script src="https://carbonbot.paygreen.fr/latest/carbon-bot.min.js"></script>
```

## 2. Configure CarbonBot
You need to set dynamically your user and your token footprint.

```js
const configBot = {
    user: "",
    token: "",
    position: "left", // optionnal: left, right
    colors: { // optionnal
        primary: "#28588a",
        primaryLight: "#d1ebff",
    },
    link: "https://my-website.com/my-engagements",
    shopName: "My shop"
};
```

## 3. Configure ResquestHandler
Set your environement to PROD ("https://api-climatekit.paygreen.fr") or SANDBOX ("https://sb-api-climatekit.paygreen.fr").

```js
const configRequest = {
    endpoint: "https://api-climatekit.paygreen.fr",
    testMode: false // 
};
```

## 4. Last step
You need to init your carbonBot by passing all your parameters:

```js
carbonBot.init(configBot,configBlock,configRequest,translations);
```