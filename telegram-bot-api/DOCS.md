# Home Assistant App: Telegram Bot API

Run your own instance of the Telegram Bot API server.

Overview:
1. [Create Telegram application](https://core.telegram.org/api/obtaining_api_id) to obtain `api_id` and `api_hash`.
2. In Home Assistant, Install, Configure and then Start the app.
3. In Home Assistant (`2026.2` or later), configure the Telegram bot integration to use the API endpoint of the app (<kbd>http://96e39688-telegram-bot-api:8081</kbd>).

You do not need to make any changes to your existing Telegram bot automations or scripts.

Note: The app has read-only access to your `media` folder.

## Pre-requisites

Before you begin, you will need to [create your Telegram application](https://core.telegram.org/api/obtaining_api_id) to obtain your `api_id` and `api_hash` which will be required for configuration later.

## Installation

1. On your Home Assistant, go to <kbd>Settings</kbd> > <kbd>Apps</kbd> > <kbd>App store</kbd>.
2. Click on the <kbd>...</kbd> icon then <kbd>Repositories</kbd>.
3. In the <kbd>Add</kbd> field, specify this repository's URL `https://github.com/avbor/hassio-apps` and then click <kbd>+ Add</kbd>.
4. Refresh the page. You should see a new app named <kbd>Telegram Bot API</kbd>. Note: If you do not see the app, wait a few moments and refresh the page again.
5. Click on the app then click <kbd>Install</kbd>. Wait a few minutes for it to finish downloading.

Once you have successfully installed the app, continue with the configuration below.

## Configuration

Refer to the [Pre-requisites](#pre-requisites) section if you have not created your Telegram application.

Configure the options below and then click <kbd>Save</kbd>.\
Click <kbd>Restart</kbd> if prompted.

After you have completed your configuration, continue with the Telegram Bot Integration Set-up to configure your Home Assistant Telegram Bot to connect to the local API instead of the official Telegram API server (https://api.telegram.org).

### General settings:

#### Option: `api_id`

Obtained from https://my.telegram.org/apps.

#### Option: `api_hash`

Obtained from https://my.telegram.org/apps.

#### Option: `log_level`

The `log_level` controls the verbosity of the log output.
Possible values are:
  - `1` - Error. Default.
  - `2` - Warning. Shows resource usage.
  - `3` - Info. Shows HTTP requests.
  - `4` - Debug

#### Option `stat_enabled`

This option allows you to control the HTTP endpoint to obtain internal server statistics on port `8082/tcp`.\
Enabled by default and accessible via the ingress network (in Home Assistant web interface).

### Proxy configuration:

#### Option: `prx_type`

Proxy type, can be one of `mtproto`, `socks5`, `http`.

#### Option: `prx_server`

Proxy server name (`FQDN` or `IP`).

#### Option: `prx_port`

Proxy port (i.e. `443`, `1080`, `8080`, etc).

#### Option: `prx_username`

Proxy username, used with `socks5`, `http` proxies.

#### Option: `prx_password`

Proxy password, used with `socks5`, `http` proxies.

#### Option: `prx_secret`

MTProxy secret (also supports secrets with dd... and ee... prefixes).

#### Configuration Example

The following is an example yaml configuration.
You must replace `api_id` and `api_hash` with your own values.

```
api_id: "12345678"
api_hash: 1234567890abcdef1234567890abcdef
log_level: 1
stat_enabled: true
proxy:
  prx_type: mtproto
  prx_server: my.mtproxy.com
  prx_port: 443
  prx_secret: ee4b67f8e98220d0ef3f388946b119d8dc73696d706c652d68612e4264
```

## Telegram Bot API Endpoint

Note: You should have already installed, configured and started the app.

The app exposes an endpoint which can be reached using the following URLs:
- `http://96e39688-telegram-bot-api:8081`\
Used within Home Assistant (telegram_bot integration for example).

Or, if you enable external port in App settings:

- `https://YOUR-HA:8081` or `http://homeassistant.local:8081`\
Replace *YOUR-HA* with your Home Assistant hostname.

## Telegram Bot Integration Configuration

This section assumes that you have already set-up the Telegram bot integration.
If you have not done so, please refer to the [Telegram bot documentation](https://www.home-assistant.io/integrations/telegram_bot).

This configuration requires Home Assistant `2026.2` or later.

To configure your Telegram bot to use your own Telegram bot API server instance (this app), do the following:
1. On your Home Assistant, go to <kbd>Settings</kbd> > <kbd>Devices & services</kbd>.
2. Click on <kbd>Telegram bot</kbd>
3. Click on the gear icon of the Telegram bot to display the options for the config entry.
4. In the API endpoint field, specify the endpoint of the app: \
`http://96e39688-telegram-bot-api:8081/bot`\
 and click <kbd>Submit</kbd>.

For more details, please refer to the documentation: https://www.home-assistant.io/integrations/telegram_bot/#configuration

## FAQs

### Why would I want to use this over the official server `https://api.telegram.org`?

Running your own server has advantages such as larger file size limits for messages and faster response times.
For more details, please refer to [using a local bot API server](https://core.telegram.org/bots/api#using-a-local-bot-api-server) in the official documentation.

### Can I chat with other users on other Telegram bot API servers?

Yes, because all Telegram bot API servers connect to the same set of Telegram MTProto servers.

## Troubleshooting

### Server error: `Can't parse as an integer string`

You may observe the following in the app logs:
```
/usr/local/bin/telegram-bot-api: Can't parse as an integer string
```

The error occurs because the value of `api_id` is invalid or too long.

To resolve this issue, update `api_id` accordingly in your configuration and restart the app.

### Client error: `Unauthorized: invalid api-id/api-hash`

This error may be encountered by Telegram clients:
```
{
  "ok":false,
  "error_code": 401,
  "description": "Unauthorized: invalid api-id/api-hash"
}
```

The error occurs because `api_id` and/or `api_hash` is invalid.

To resolve this issue,
1. Check your `api_id` and `api_hash` at https://my.telegram.org/apps.
2. Update the app configuration accordingly and restart the app.

## Support

Questions? Issues?

Please open an [issue](https://github.com/avbor/hassio-apps/issues),\
or, ask in [this](https://t.me/simple_ha) Telegram group (primary on Russian).
