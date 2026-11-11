# Bayline 3D site

Pages:

| File | What it is |
|---|---|
| `index.html` | Home page: unlock box, how access works, contact list |
| `viewer.html` | The 3D viewer (locked until the password is entered) |
| `guide.html` | What every button, slider and readout does |
| `404.html` | Not-found page |
| `site-config.js` | Your email, contact list, and the password hash |
| `model.glb` | The BMW M4 GT3 sample |

Default password: **Bayline-GT3-2026**. Change it before you share the site (see below).

## Host it free

You cannot get a free `.com`. All three hosts below give you a free address on their own domain, such as `bayline3d.netlify.app`. A custom domain such as `bayline3d.com` costs money (about 10 USD a year) and can be attached later in the host's settings.

VISIT OUR WEB PAGE AT: 
https://bayline3d.netlify.app



### Cloudflare Pages
1. Cloudflare dashboard, Workers & Pages, Create, Pages, Upload assets.
2. Name the project and upload this folder. Your address is `yourname.pages.dev`.

### GitHub Pages
1. Create a repository named `yourusername.github.io` and upload these files to it.
2. Settings, Pages, deploy from the `main` branch. The address is `yourusername.github.io`.

## Change the password

With Node installed, run this in the site folder, then upload the site again:

```
node set-password.js "your new password"
```

Without Node, compute SHA-256 of `bayline-3d::` followed by your password (any online SHA-256 tool works) and paste the result into `hash` in `site-config.js`.

## Add or change contacts

Edit the `contacts` list in `site-config.js`. Each row has a `label`, `value`, `href`, and `note`.

## Know the limits of the lock

The lock is a front-end gate. It stops casual visitors from opening the viewer page, but the password hash and the model file are public files on your host. Someone who knows the address `/model.glb` can download the model without the password, and a determined person can bypass the check in their browser. If the model itself must stay private, use host-side protection instead, such as Cloudflare Access (free for small groups) or Netlify's paid password protection, and do not upload the model to a public site.
