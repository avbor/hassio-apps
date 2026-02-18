# Home Assistant App: Telegram Bot API

![GitHub Release][releases-shield] [![License][license-shield]](LICENSE.md)
![Supports amd64 Architecture][amd64-shield] ![Supports aarch64 Architecture][aarch64-shield]

## About

Based on [hanwg](https://github.com/hanwg/telegram-bot-api) and [Seed680](https://github.com/Seed680/telegram-bot-api) work.
Thanks, guys!

This app allows you to run your own [Telegram Bot API server](https://github.com/tdlib/telegram-bot-api) instead of using the official server `https://api.telegram.org`.

If you switch to a local Bot API server, your bot will be able to:

- Download files without a size limit.
- Upload files up to 2000 MB.
- Upload files using their local path and the file URI scheme.
- Use an HTTP URL for the webhook.
- Use any local IP address for the webhook.
- Use any port for the webhook.
- Set max_webhook_connections up to 100000.
- Receive the absolute local path as a value of the file_path field without the need to download the file after a getFile request.

**In addition, this application allows you to use proxy server (MTProto, SOCKS5 or HTTP) to connect to the Telegram infrastructure.**

[Documentation](https://github.com/avbor/hassio-apps/blob/main/telegram-bot-api/DOCS.md)

The app is built using the [avbor/ha-telegram-bot-api](https://github.com/avbor/ha-telegram-bot-api) image which uses the [official source](https://github.com/tdlib/telegram-bot-api) and some additions from [Seed680](https://github.com/Seed680/telegram-bot-api) for proxy setup.

[releases-shield]: https://img.shields.io/badge/version-v9.4.1-blue.svg
[license-shield]: https://img.shields.io/github/license/avbor/hassio-apps.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
