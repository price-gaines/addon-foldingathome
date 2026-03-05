# Home Assistant Community Add-on: Folding@home

Folding@home (FAH or F@h) is a distributed computing project for performing
molecular dynamics simulations of protein dynamics. Its initial focus was on
protein folding but has shifted to more biomedical problems, such as Alzheimer's
disease, cancer, Ebola and the coronavirus.

The project uses the idle processing resources of personal computers owned by
volunteers who have installed the software on their systems.

Now you can donate the idle time of your Home Assistant instance to the
Folding@home project, helping to fight these diseases.

Join the Home Assistant Folding@home team! (id: 247478)

Team stats: <https://stats.foldingathome.org/team/247478>

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Home Assistant add-on.

1. Click the Home Assistant My button below to open the add-on on your Home
   Assistant instance.

   [![Open this add-on in your Home Assistant instance.][addon-badge]][addon]

1. Click the "Install" button to install the add-on.
1. Start the "Folding@home" add-on.
1. Check the logs of the "Folding@home" to see if everything went well.
1. Open the Web UI.

**Note**: The previous official release of this add-on would start folding immediately on first start using the username `Anonymous` and the Home Assistant team number (id: 247478).

This updated version does not support that anonymous auto-start behavior. To reliably start folding, you must provide all required configuration fields (see below). The team number can remain auto-filled for convenience.

Team stats: <https://stats.foldingathome.org/team/247478>

## Configuration


**Note**: _Remember to restart the add-on when the configuration is changed._

The identity/linking options below (`user`, `team`, `passkey`, `account_token`, `machine_name`) are required for this updated v8.5.5 build to reliably start folding and be controllable via Web Control.

Example add-on configuration:

```yaml
log_level: info
user: "your_username"
team: 247478
passkey: "your_passkey"
account_token: "your_account_token"
machine_name: "your_machine_name"
```

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `user`

Folding@home donor username (for credit/stats).

### Option: `team`

Folding@home team number (for credit/stats).

### Option: `passkey`

Folding@home passkey for your donor identity.

### Option: `account_token`

Folding@home Account Token used to link this node for v8.5 Web Control.

### Option: `machine_name`

Machine name shown for this node in Folding@home Web Control.

## Embedding into Home Assistant

Previous versions of this add-on exposed an older local Web Control that could be embedded in Home Assistant using the `panel_iframe` integration.

With the current v8.5.5 account-based Web Control, embedding is no longer recommended. In testing, Home Assistant's iframe integration does not provide a reliable login/control workflow for Folding@home Web Control. The login flow is designed for direct browser interaction and account-based session handling, which does not behave reliably when loaded inside an embedded iframe.

For that reason, this add-on should be accessed directly through its Web UI rather than embedded into the Home Assistant frontend.

## Known issues and limitations

- This add-on only runs on 64-bits intel-based computers.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## Support

Got questions?

You have several options to get them answered:

- The [Home Assistant Community Add-ons Discord chat server][discord] for add-on
  support and feature requests.
- The [Home Assistant Discord chat server][discord-ha] for general Home
  Assistant discussions and questions.
- The Home Assistant [Community Forum][forum].
- Join the [Reddit subreddit][reddit] in [/r/homeassistant][reddit]

You could also [open an issue here][issue] GitHub.

## Authors & contributors

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License

MIT License

Copyright (c) 2020-2024 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[addon-badge]: https://my.home-assistant.io/badges/supervisor_addon.svg
[addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=a0d7b954_foldingathome&repository_url=https%3A%2F%2Fgithub.com%2Fhassio-addons%2Frepository
[contributors]: https://github.com/hassio-addons/addon-foldingathome/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord]: https://discord.me/hassioaddons
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-folding-home/180496?u=frenck
[frenck]: https://github.com/frenck
[issue]: https://github.com/hassio-addons/addon-foldingathome/issues
[reddit]: https://reddit.com/r/homeassistant
[releases]: https://github.com/hassio-addons/addon-foldingathome/releases
[semver]: http://semver.org/spec/v2.0.0.htm
