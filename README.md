# Shared Build Cache Heroku Buildpack

This buildpack allows a Heroku app to copy over the build cache from another Heroku app on its initial build. It was created to speed up Review App deployments for a large Rails monolith that can take up to 20 minutes to build from a cold build cache.

Without a build cache, a Rails app built on Heroku has to:

* Download and install all bundler gems
* Compile all Sprockets assets from scratch (no existing `public/assets` and no `tmp/cache/assets`)
* Compile all webpacker assets, including downloading and installing `node_modules`

## Configuration

Add the name of the Heroku app containing the build cache you want to share, to the app(s) you want to use it on their initial build. If you're using Review Apps, you probably want this in `app.json`.

```
SHARED_BUILD_CACHE_APP_NAME=my-staging-app
```

---

Made with ✨by the SRE team at [Kajabi](https://kajabi.com)
