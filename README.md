PayGreen - CarbonBot - Widget JS
===========

![Carbon Bot presentation](https://github.com/PayGreen/carbon-bot-doc/blob/main/doc/presentation.jpg)

> **ClimateKit documentation**
> In order to understand how to create a carbon footprint and get your tokens, you can to check our ClimateKit API [documentation](https://api-climatekit.paygreen.fr/documentation/climate)


## 1. Adding JS script
Add the javascript file in your code:
```html
<script src="https://carbonbot.paygreen.fr/1.0.0/carbon-bot.min.js"></script>
```

## 2. Retrieve the user id and footprint
You need to find your user and your token footprint.

Retrieve the user id:
```shell
curl --location --request GET 'http://api-climatekit.paygreen.fr/account/me/user/me' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer my_bearer'
```

To retrieve the footprint, you must have created it first:  [documentation](https://api-climatekit.paygreen.fr/documentation/climate#tag/CarbonFootprint/paths/~1carbon~1footprints/post)

## 3. Init CarbonBot
You need to init your CarbonBot by passing all your parameters:

```js
carbonBot.init({
    endpoint: "https://api-climatekit.paygreen.fr",
    testMode: false,
    bot: {
        user: "user_id_here",
        token: "footprint_here",
        position: "inline", // optionnal: left, right
        colors: { // optionnal
            primary: "#a5211f",
        },
        engagementLink: "https://my-website.com/my-engagements",
        shopName: "My shop name",
    }
});
```