# avbor's Home Assistant Apps (Addons)

### Local [Telegram Bot API](https://github.com/tdlib/telegram-bot-api/) Server

[Using a Local Bot API Server](https://core.telegram.org/bots/api#using-a-local-bot-api-server)

You can run it locally and send the requests to your own server instead of https://api.telegram.org.\
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

[HA App Documentation](https://github.com/avbor/hassio-apps/blob/main/telegram-bot-api/DOCS.md)
