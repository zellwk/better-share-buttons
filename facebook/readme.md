## Styling the share button

Use the following HTML.

```html
<button data-share-button="facebook">
  <svg><!-- Facebook SVG --></svg>
  <span>Share on Facebook</span>
</button>
```

Include `share-button.css` and `facebook.css` for default styles. You can customize the button by writing other CSS rules.

## Steps for making the share dialog work

Import the Facebook SDK. Place this somewhere in the page you want to use the Facebook share button.

```js
<script
  async
  crossorigin='anonymous'
  src='https://connect.facebook.net/en_US/sdk.js'
></script>
```

If you want to create customizable share dialog, you need to [create a Facebook app](https://developers.facebook.com/docs/development/create-an-app). This is painless so just go make one if you need to.

Once you have one, you can initialize Facebook SDK with your `appID`.

If you already have a Facebook app, you can get get your `appID` from the [Developer Portal](https://developers.facebook.com/apps/).

```html
<script>
  window.fbAsyncInit = function () {
    FB.init({ appId: 'YOUR_APP_ID', version: 'v13.0' })
  }
</script>
```

Trigger the share dialog on click.

Note: You cannot pre-fill Facebook's share dialog with any text. The user must generate their own text.

```js
window.fbAsyncInit = function () {
  FB.init(/*...*/)

  const facebookButton = document.querySelector(
    '[data-share-button="facebook"]'
  )

  facebookButton.addEventListener('click', event => {
    FB.ui(
      {
        method: 'share',
        href: 'URL_TO_SHARE'
      },
      function () {}
    )
  })
}
```
