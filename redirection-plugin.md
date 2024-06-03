# Redirection Plugin

The free [Redirection plugin comes pre-installed](https://wordpress.org/plugins/redirection/) for you to easily set up redirects between pages, internal and external.

When using the Redirecting plugin in Astro JS, it creates a meta redirect rather than an SEO-friendly 301 redirect because static sites handle redirections differently.

> For creating SEO-friendly redirects, see the [SEO guide](seo.md)

## Adding A Redirect

Use the "add new redirection" form to create a new redirect.

<img src="https://github.com/astrowp/docs/assets/170225022/5cc57504-e61c-4a6a-8ba5-8b3f10772ce3" width="750px" />

In its most basic form you need to enter a source URL (the URL you are redirecting from) and a target URL (the URL you are redirecting to).

The source URL is generally relative to your site. This means, for example, if the URL you want to redirect from is https<span>://</span>myexample.com/old-url, and Redirection is installed on https<span>://</span>myexample.com then the source is /old-url – it is relative to your domain.

The target can be any URL, relative or otherwise.

The source URL cannot contain a hash #. This is not sent to the server and it is not possible to match against it. This is a general web limitation and not one imposed by Redirection.

## Editing a Redirect

Once you’ve created a redirect it will be added to your list. When you hover over the newly created redirect you will see links appear beneath it:

![image](https://github.com/astrowp/docs/assets/170225022/8db6f703-f9c8-4446-98d4-727ce89e5fb0)

Press the edit link to edit the redirect in exactly the same way you added it.

## Enabling, Disabling, and Deleting

Deleting a redirect removes it from Redirection and it will no longer be active.

A disabled redirect means the redirect still exists in Redirection, but it’s not active. Use this to temporarily disable the redirect without deleting it.

Enabling a redirect re-activates a disabled redirect.
