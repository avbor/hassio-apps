# avbor's Home Assistant Apps (Addons)

![Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE.md)

## About

This repository contains primarily those Home Assistnt Apps that I use myself.

Use the following URL to add this repository:

```txt
https://github.com/avbor/hassio-apps
```
Or, simply click the button below to add it automatically:

[![Add Repository](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Favbor%2Fhassio-apps)

## Add-ons provided by this repository

### &#10003; [Telegram Bot API](https://github.com/tdlib/telegram-bot-api/) Server

![GitHub Release][telegram-bot-api-releases-shield] ![Supports amd64 Architecture][amd64-shield] ![Supports aarch64 Architecture][aarch64-shield]

With this app you can send the requests to your own server instead of https://api.telegram.org.

If you switch to a using a [local Bot API server](https://core.telegram.org/bots/api#using-a-local-bot-api-server), your bot will be able to:

- Download files without a size limit.
- Upload files up to 2000 MB.
- Use an HTTP URL for the webhook.
- Use any local IP address for the webhook.
- Use any port for the webhook.
- Set max_webhook_connections up to 100000.

and more.

**In addition, this application allows you to use proxy server (MTProto, SOCKS5 or HTTP) to connect to the Telegram infrastructure.**

[Documentation](https://github.com/avbor/hassio-apps/blob/main/telegram-bot-api/DOCS.md)

---

[telegram-bot-api-releases-shield]: https://img.shields.io/badge/version-v9.4.1-blue.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[license-shield]: https://img.shields.io/github/license/avbor/hassio-apps.svg
[maintenance-shield]: https://img.shields.io/maintenance/yes/2026.svg