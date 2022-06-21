PayGreen - CarbonBot - Widget JS
===========

![Carbon Bot presentation](https://github.com/PayGreen/carbon-bot-doc/blob/main/doc/presentation.jpg)

> **ClimateKit documentation**
> In order to understand how to create a carbon footprint and get your tokens, you can to check our ClimateKit API [documentation](https://api-climatekit.paygreen.fr/documentation/climate)


## 1. Adding JS script
Add the javascript file in your code:
```html
<script src="https://carbonbot.paygreen.fr/latest/carbon-bot.js"></script>
```

In order to import the contribution banner in your checkout page, you need to add this code:
```html
<div data-paygreen-carbon-banner></div>
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
    locale: "fr", // fr, en, es
    shopName: "My shop name",
    bot: {
        user: "user_id_here",
        token: "footprint_here",
        position: "right", // optionnal: left, right
        colors: { // optionnal
            primary: "#a5211f",
        },
        engagementLink: "https://my-website.com/my-engagements", // optionnal
        displayed: true, // optionnal
    },
    banner: { // optionnal: allows you to configure the contribution banner
        addContributionAction: null, // set the action to add a contribution to cart, price in param: actionContribution(price)
        removeContributionAction: null,  // set the action to remove a contribution from a cart
        hasContributionInCart: false, // use the correct action if a contribution is in the cart or not
        displayed: true, // optionnal
    },
    cart: {
        price: 2000, // current cart price in cent
        weight: 5, // current cart weight in kg
        shippingFromAddress: {
            street: '1 rue de Paris',
            city: 'Paris',
            postcode: '75001',
            country: 'France'
        },
        transportationExternalId: "1-28022",
        deliveryService : null
    },
    translations: { // optionnal, variables are automatically replaced: {shopName}, {estimatedPrice},...
        "en": {
            title: "My purchase contributing to carbon neutrality",
            engagementDescription: "{shopName} finances GHG reduction and sequestration projects up to the amount of your emissions. 🎉",
            shipping: "Your carrier compensates for its own emissions: you only have to pay {estimatedPrice} instead of {priceWithShipping} to make your purchase carbon neutral!",
            offset: "Fund a climate project up to {estimatedPrice}",
            goal: "Contribute to carbon neutrality"
        },
        "fr": {
            title: "Mon achat contribuant à la neutralité carbone !",
            engagementDescription: "{shopName} vous propose de compenser votre impact carbone. 🎉",
            shipping: "Votre transporteur compense ses propres émissions : vous n’avez que {estimatedPrice} au lieu de {priceWithShipping} à verser pour que votre achat contribue à la neutralité carbone !",
            offset: "Financer un projet climatique à hauteur de {estimatedPrice}",
            goal: "Contribuer à la neutralité carbone"
        },
        "es": {
            title: "Mi compra contribuye a la neutralidad del carbono",
            engagementDescription: "{shopName} financia proyectos de reducción y secuestro de GEI hasta el importe de sus emisiones. 🎉",
            shipping: "Su transportista compensa sus propias emisiones: ¡sólo tiene que pagar {estimatedPrice} en lugar de {priceWithShipping} para que su compra sea neutra en carbono!",
            offset: "Financiar un proyecto climático de hasta {estimatedPrice}",
            goal: "Contribuir a la neutralidad del carbono"
        },
    },
});

carbonBot.updateConfig({ // you can also use this function to update carbonBot configuration:
    testMode: true,
    bot: {
        user: "1784",
        footprint: "6187e3c7-a510-4d28-98ca-6fb1f37646a8"
    }
});
```
