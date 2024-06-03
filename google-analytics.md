# How to Install Google Analytics Tracking

Here is how you can integrate Google Analytics with Astro JS and ensure that events are sent on navigation.

## Get Your Google Analytics Tracking ID

Ensure you have a Google Analytics account.

Copy your tracking ID (format: G-XXXXXXXXXX).

## Edit /src/config/scripts.astro

```
 ── src
    └── config/
        └── scripts.astro
```

Navigate to your project’s src directory.

Open the config folder.

Find and edit the ```scripts.astro``` file:

Add the following code to the scripts.astro file, **replacing G-XXXXXXXXXX** with your actual tracking ID:

```
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
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
      gtag("config", "G-XXXXXXXXXX");
    },
    { once: false },
  );
</script>
```

**Replace G-XXXXXXXXXX** with your Google Analytics tracking ID.

## Commit Your Changes

Save the changes to scripts.astro.

Commit the changes to your repository.
