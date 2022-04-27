# Pages and Sections


## Multi-Page Support

You can have additional pages within your dashboard, with each having it's own config file. The config files for sub-pages can either be stored locally, or hosted separately. A link to each additional page will be displayed in the navigation bar.

Note that the only top-level fields supported by sub-pages are `pageInfo` and `sections`. The `appConfig` and `pages` will always be inherited from your main `conf.yml` file. Other than that, sub-pages behave exactly the same as your default view, and can contain sections, items, widgets and page info like nav links, title and logo.

### Using Local Sub-Pages

To get started, create a new `.yml` config file for your sub-page, placing it within `/app/public`. Then within your primary `conf.yml`, choose a name, and specify the path to the new file.

For example:

```yaml
pages:
- name: Networking Services
  path: 'networking.yml'
- name: Work Stuff
  path: 'work.yml'
```

### Using Remote Sub-Pages

Config files don't need to be local, you can store them anywhere, and data will be imported as sub-pages on page load.

For example:

```yaml
pages:
- name: Getting Started
  path: 'https://snippet.host/tvcw/raw'
- name: Homelab
  path: 'https://snippet.host/tetp/raw'
- name: Browser Startpage
  path: 'https://snippet.host/zcom/raw'
```

There are many options of how this can be used. You could store your config within a Git repository, in order to easily track and rollback changes. Or host your config on your NAS, to have it backed up with the rest of your files. Or use a hosted paste service, for example [snippet.host](https://snippet.host/), which supports never-expiring CORS-enabled pastes, which can also be edited later.

You will obviously not be able to write updates to remote configs through the UI editor, but you can still make and preview changes, then use the export menu to get a copy of the new config, and modify the original source manually.
The config file must, of course be accessible from within Dashy. If your config contains sensitive info (like API keys, credentials, secret URLs, etc), take care not to expose it to the internet.

The following example shows creating a config, publishing it as a [Gist](https://gist.github.com/), copying the URL to the raw file, and using it within your dashboard.

<p align="center">
  <img width="700" alt="Public config in a gist demo"
    src="https://i.ibb.co/55jm3LG/how-to-use-remote-config-sub-page.gif"
  />
</p>
