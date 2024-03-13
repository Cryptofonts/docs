# Quickstart guide

If you are looking to try out Cryptofonts you can use our CDN instead of hosting it yourself.

Simply add the current one-liner at the `head` of your document to use the latest version.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/monzanifabio/cryptofont/cryptofont.css">
```

If you find yourself stuck, or it’s the first time using a Webfont, you can download our quickstart template to see how it works.

{% embed url="https://cryptofonts.com/getting-started-template.zip" %}

If you want to use a previous version of Cryptofonts visit this section for more information.

[previous-versions.md](previous-versions.md "mention")

***

## Npm install

Cryptofonts is also available as an npm package.

To install run the following command from within your project.

```
npm i @cryptofonts/cryptofont
```

***

## Manual install

If you decide to manually install Cryptofonts and host it on your website, download the latest release of Cryptofonts from GitHub to get started.

[Download the latest release from GitHub](https://github.com/monzanifabio/cryptofont/releases)

### **1. Move the CSS and web fonts into your project.**

Copy the entire \*\*`webfonts`\*\*folder and the \*\*`cryptofont.css`\*\*into your project’s static assets directory (or where ever you prefer to keep front end assets or vendor stuff).

### **2. Reference the CSS**

Add a reference to the \*\*`cryptofont.css`\*\*styling file into the `<head>`of each template or page that you want to use Crypto Font on. Pay attention to the pathing of your project and where you moved the files to in the previous step.

```html
<head>
	<!--CryptoFont-->
	<link href="cryptofont.css"rel="stylesheet">
</head>
```

### **3. Place icons in your UI’s markup**

With the references complete, you can now start placing icons in your HTML’s `<body>`

We recommend using a consistent HTML element, like an `<i>`

You can place Crypto Fonts icons just about anywhere using the CSS Prefix `cf` and the crypto ticker.

```html
<body>
	<!--some icons-->
	<i class="cf cf-btc"></i>  <!-- Bitcoin -->
	<i class="cf cf-eth"></i>  <!-- Ethereum -->
	<i class="cf cf-ltc"></i>  <!-- Litecoin -->
</body>
```
