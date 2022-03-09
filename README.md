# embroider-in-repo-addons

This is a sample app showing that Embroider includes non-Fastboot
dependencies in the `dist/package.json`. A side effect of this is that
in-repo addons that are named with a @scope, can fail to install.

## Try it out

### Working Case

```bash
npm run build
cd dist
npm i
## success

# you can also see that dependencies don't include `lib/@foo/my-thing` or `lib/my-thing`.
cat package.json | jq '.dependencies'
```

### Failing Case

```bash
npm run build:embroider
cd dist
npm i # :(

# you can also see that dependencies DO include `lib/@foo/my-thing` or `lib/my-thing`.
cat package.json | jq '.dependencies'
```
