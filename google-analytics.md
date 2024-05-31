# How to Install Google Analytics Tracking

Here is how you can integrate Google Analytics with Astro JS and ensure that events are sent on navigation.

## Get Your Google Analytics Tracking ID

Before proceeding, make sure you have a Google Analytics account and copy the G-XXXXXXXXXX tracking ID.

## Edit /src/config/scripts.astro

```
 ── src
    └── config/
        └── scripts.astro
```

Go to ```/src/config/scripts.astro``` edit this file, and simply paste in your tracking ID.

```
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script> <----- HERE
<script is:inline>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
</script>
<script is:inline>
  document.addEventListener(
    "astro:page-load",
    () => {
      gtag("js", new Date());
      gtag("config", "G-XXXXXXXXXX"); <----- AND HERE
    },
    { once: false },
  );
</script>
```

**Replace G-XXXXXXXXXX** with your tracking ID.

Then Commit changes.
