## Styling the share button

Use the following HTML.

```html
<button data-share-button="twitter">
  <svg><!-- Twitter SVG --></svg>
  <span>Share on Twitter</span>
</button>
```

Please include `share-button.css` and `twitter.css` for default styles. You can customize the button by writing other CSS rules.

## Steps for making the share button work

Import Twitter's share widget. Place this somewhere in the page you want to use the Twitter share button.

```js
<script
  async
  src='https://platform.twitter.com/widgets.js'
  charset='utf-8'
></script>
```

Trigger the share intent on click.

```html
<script>
  const twitterShareButton = document.querySelector(
    '[data-share-button="twitter"]'
  )

  twitterShareButton.addEventListener('click', event => {
    const link = document.createElement('a')
    const params = {
      text: 'Text to appear on the tweet',
      url: 'URL_TO_SHARE'
    }
    const endpoint = 'https://twitter.com/intent/tweet'

    const searchParams = new URLSearchParams(params)
    const href = `${endpoint}/?${searchParams.toString()}`
    link.href = href
    link.click()
  })
</script>
```
