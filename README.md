PayGreen - CarbonBot - Widget JS
===========

![Carbon Bot presentation](https://github.com/PayGreen/carbon-bot-doc/blob/main/doc/presentation.jpg)

> **ClimateKit documentation**
> In order to understand how to create a carbon footprint and get your tokens, you can to check our ClimateKit API [documentation](https://api-climatekit.paygreen.fr/documentation/climate)


## 1. Adding JS script
Add the javascript file in your code:
```html
<script src="https://carbonbot.paygreen.fr/1.0.3/carbon-bot.js"></script>
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
        shopName: "My shop name",
        cartPrice: 1250, // optionnal: current cart price in cent
        position: "right", // optionnal: left, right
        colors: { // optionnal
            primary: "#a5211f",
        },
        engagementLink: "https://my-website.com/my-engagements", // optionnal
        translations: { // optionnal, shopName is automatically replaced
            "en": {
                title: "My carbon neutral purchase thanks to {shopName}",
                engagementDescription: "{shopName} finances GHG reduction and sequestration projects up to the amount of your emissions. 🎉",
            },
            "fr": {
                title: "Mon achat neutre en carbone grâce à {shopName}",
                engagementDescription: "{shopName} finance des projets de réduction et de séquestration de GES à hauteur de vos émissions. 🎉",
            }
        },
    }
});
```
