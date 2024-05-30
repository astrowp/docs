# SEO

## Permanent 301 Redirects


### Vercel

Create a new file on the root folder for the repo called ```vercel.json```

```
{
"redirects": [
	{
			"source": "/play/:path*(/)?",
			"destination": "/"
	},
	{
			"source": "/company/",
			"destination": "/"
	},
	{
			"source": "/chat/",
			"destination": "https://discord.gg/grF4GTXXYm"
	},
	{
			"source": "/deprecated/resolve/",
			"destination": "https://docs.astro.build/en/migrate/#deprecated-astroresolve"
	},
	{
			"source": "/v0.21/",
			"destination": "/blog/astro-021-release/"
	},
	{
			"source": "/hack/",
			"destination": "https://astroinc.notion.site/FRIDAY-Astro-1-0-Hackathon-9fb3499b375e4b01b88b080fd918b184"
	},
	{
			"source": "/resources/image-templates/",
			"destination": "https://www.figma.com/community/file/1182357255394426899"
	},
	{
			"source": "/newsletter/",
			"destination": "/newsletter/signup"
	}
	]
}
```

For more information, see [Vercel's redirects documentation](https://vercel.com/docs/edge-network/redirects#static-redirects)

### Netlify

Create a new file on the root folder for the repo called ```netlify.toml```

```
[[redirects]]
  from = "/blog/"
  to = "/posts/"
  status = 301
  force = true

[[redirects]]
  from = "https://somenetlifysite.netlify.app"
  to = "https://mycustomdomain.com"
  status = 301
  force = true
```

For more information, see [Netlify's redirects documentation](https://docs.netlify.com/configure-builds/file-based-configuration/#redirects)

### DigitalOcean

Go to the App Settings of your project, and in **HTTP Routes Redirect** is where you create and configure redirects.

![image](https://github.com/astrowp/docs/assets/170225022/710f46d6-2f82-4e86-a859-85d2e66e6650)

- Route Path: The existing path to redirect traffic from
- Redirect URI: The path of the destination domain to redirect traffic to
- Redirect Authority: The destination domain to redirect traffic to. If left empty, the requesting authority is used
- Redirect Status Code: The HTTP status code to return when redirecting the user. Valid values are 300, 301, 302, 303, 304, 307, and 308. If not specified, it defaults to 302 (temporary redirect)
- Redirect Port: The port of the destination URI to which traffic should be sent. If not specified, the value is omitted from the request or used to send traffic to the port of the original request
- Redirect Scheme: The URI scheme the redirect uses. Must either be HTTP or HTTPS. Defaults to HTTPS if not specified
- In the example above, https<span>://</span>starfish-app-6r6mv.ondigitalocean.app/glossary/what-is-wp/ is permanently "301" redirected to https<span>://</span>starfish-app-6r6mv.ondigitalocean.app/glossary/what-is-wp/

For more information, see [DigitalOcean's redirects documentation](https://docs.digitalocean.com/products/app-platform/how-to/url-rewrites/)
