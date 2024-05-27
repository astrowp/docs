# How to Install Google Analytics Tracking

Here is how you can integrate Google Analytics with Astro JS and ensure that events are sent on navigation.

## Step 1: Get Your Google Analytics Tracking ID

Before proceeding, make sure you have a Google Analytics account and get  the tracking ID for your website.

## Step 2: Copy the Following Code

Copy this code.

```
<script 
  async 
  src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"
></script>
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
    { once: false }
  );
</script>
```

## Step 3: Replace G-XXXXXXXXXX with Your Tracking ID

Replace "G-XXXXXXXXXX" in the code with your actual Google Analytics tracking ID.

## Step 4. Paste into layout.astro

Then, edit the file ```layout.astro``` in ```src/layouts/layout.astro```, go to line 91 add in the script tag.
