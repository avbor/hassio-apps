# Home Assistant App: Telegram Bot API

![GitHub Release][releases-shield] [![License][license-shield]](LICENSE.md)

![Supports amd64 Architecture][amd64-shield] ![Supports aarch64 Architecture][aarch64-shield]

Telegram Bot API server for Home Assistant.

[Documentation](https://github.com/avbor/hassio-apps/blob/main/telegram-bot-api/DOCS.md)

## About

Based on [hanwg](https://github.com/hanwg/telegram-bot-api) and [Seed680](https://github.com/Seed680/telegram-bot-api) work.
Thanks, guys!

This app allows you to run your own [Telegram Bot API server](https://github.com/tdlib/telegram-bot-api) instead of using the official server `https://api.telegram.org`.
With additional proxy support between local and Telegram servers. MTProto, SOCKS5 and HTTP proxies are supported.
Running your own server has advantages such as larger file size limits for messages and faster response times.
For more details, please refer to [using a local bot API server](https://core.telegram.org/bots/api#using-a-local-bot-api-server) in the official documentation.

The app is built using the [avbor/telegram-bot-api](https://github.com/avor/telegram-bot-api) image which uses the [official source](https://github.com/tdlib/telegram-bot-api) and some additions from [Seed680](https://github.com/Seed680/telegram-bot-api) for proxy setup.

[releases-shield]: https://img.shields.io/github/release/avbor/hassio-apps.svg
[license-shield]: https://img.shields.io/github/license/avbor/hassio-apps.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
