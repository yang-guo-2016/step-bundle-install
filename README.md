# bundle-install

This is an _smart_ version of the `bundle install` command that stores
downloaded gems in a cache directory that is shared with future builds. This
should improve the execution time of the future builds. If bundle install
failed it will retry one more time, optionally clearing the gem path.

[![wercker status](https://app.wercker.com/status/3e287b2291a600958d7dd47ba35d9af8/m "wercker status")](https://app.wercker.com/project/bykey/3e287b2291a600958d7dd47ba35d9af8)

# Options

* `path` (optional, default: `$WERCKER_CACHE_DIR/bundle-install/`) The path which will be used to store the gem files. Leave empty to enable caching.
* `without` (optional) Exclude gems that are part of the specified named group.
* `standalone` (optional) Make a bundle that can work without the Bundler runtime.
* `binstubs` (optional) Generate bin stubs for bundled gems to ./bin.
* `clean` (optional) Run bundle clean automatically after install.
* `full-index` (optional) Use the rubygems modern index instead of the API endpoint.
* `deployment` (optional) Install using defaults tuned for deployment environments.
* `local` (optional) Do not attempt to fetch gems remotely and use the gem cache instead.
* `frozen` (optional) Do not allow the Gemfile.lock to be updated after this install.
* `jobs` (optional) Install gems parallely by starting the number of workers specified (require at least bundler `1.5`).
* `version` (optional, default: `>=1.5.2`) If no bundler is found, install
bundler with this version. Supports semver version.
* `gemfile` (optional, default: `Gemfile`) The name of the file that bundler should use as the Gemfile.
* `retry` (optional, default: `3`) Retry network and git requests that have failed.
* `clear-path` (optional, default: `true`) Before retrying a failed bundle
   install, clear the location that is used for the gems.

# Example

``` yaml
build:
  steps:
    - bundle-install
```

# License

The MIT License (MIT)

# Changelog

## 2.0.1

- Fix for failing bundle install execution

## 2.0.0

- Add `retry` to the bundle command
- Try running the bundle install command another time if it fails.
- Clear the path by default once the bundle install command fails.

## 1.1.3

- Add `gemfile` option

## 1.1.2

- Add `version` option

## 1.1.1

- Fix bug if cwd parameter is used
- Only install bundler if an Gemfile is found
- Always display bundle version information

## 1.1.0

- Update to bundler `1.5.2`
- Add `jobs` parameter.

## 0.9.4

- Remove unnecessary 'cd' commands

## 0.9.3

- Add frozen flag

## 0.9.1

- Initial release
