# Home Assistant App: Telegram Bot API

Run your own instance of the Telegram Bot API server.

Overview:
1. [Create Telegram application](https://core.telegram.org/api/obtaining_api_id) to obtain `api_id` and `api_hash`.
2. In Home Assistant, Install, Configure and then Start the app.
3. In Home Assistant (`2026.2` or later), configure the Telegram bot integration to use the API endpoint of the app:\
`http://96e39688-telegram-bot-api:8081`

You do not need to make any changes to your existing Telegram bot automations or scripts.

Note: The app has read-only access to your `media` folder.

## Pre-requisites

Before you begin, you will need to [create your Telegram application](https://core.telegram.org/api/obtaining_api_id) to obtain your `api_id` and `api_hash` which will be required for configuration later.\
If you can't create an app due to an error, refer to the [Troubleshooting](#creating-an-app-on-mytelegramorgapps-error) section.

## Installation

1. On your Home Assistant, go to <kbd>Settings</kbd> > <kbd>Apps</kbd> > <kbd>App store</kbd>.
2. Click on the <kbd>...</kbd> icon then <kbd>Repositories</kbd>.
3. In the <kbd>Add</kbd> field, specify this repository's URL `https://github.com/avbor/hassio-apps` and then click <kbd>+ Add</kbd>.
4. Refresh the page. You should see a new app named <kbd>Telegram Bot API</kbd>.\
Note: If you do not see the app, wait a few moments and refresh the page again.
5. Click on the app then click <kbd>Install</kbd>.\
Wait a few minutes for it to finish downloading.

Once you have successfully installed the app, continue with the configuration below.

## Configuration

Refer to the [Pre-requisites](#pre-requisites) section if you have not created your Telegram application.

Configure the options below and then click <kbd>Save</kbd>.\
Click <kbd>Restart</kbd> if prompted.

*This configuration requires Home Assistant `2026.2` or later:*\
After you have completed your configuration, continue with the Telegram Bot Integration Set-up to configure your Home Assistant Telegram Bot to connect to the local API instead of the official Telegram API server (https://api.telegram.org).

This can be done by reconfiguring the Telegram bot integration:

1. Go to <kbd>Settings</kbd> > <kbd>Device & Services</kbd> > <kbd>Telegram bot</kbd>.
2. Click on <kbd>...</kbd> icon and press <kbd>Reconfigure</kbd>.
3. Open <kbd>Advanced settings</kbd> section and change <kbd>API endpoint</kbd> field.
4. Complete the reconfiguration by pressing <kbd>Submit</kbd> several times.


### General settings:

#### Option: `api_id`

Obtained from <https://my.telegram.org/apps>.

#### Option: `api_hash`

Obtained from <https://my.telegram.org/apps>.

#### Option: `log_level`

The `log_level` controls the verbosity of the log output.
Possible values are:
  - `1` - Error. Default.
  - `2` - Warning. Shows resource usage.
  - `3` - Info. Shows HTTP requests.
  - `4` - Debug

#### Option: `stat_enabled`

This option allows you to control the HTTP endpoint to obtain internal server statistics on port `8082/tcp`.\
Enabled by default and accessible via the ingress network (in Home Assistant web interface).

### Proxy configuration:

#### Option: `proxy:` `prx_type`

Proxy type, can be one of `mtproto`, `socks5`, `http`.

#### Option: `proxy:` `prx_server`

Proxy server name (`FQDN` or `IP`).

#### Option: `proxy:` `prx_port`

Proxy port (i.e. `443`, `1080`, `8080`, etc).

#### Option: `proxy:` `prx_username`

Proxy username, used with `socks5`, `http` proxies.

#### Option: `proxy:` `prx_password`

Proxy password, used with `socks5`, `http` proxies.

#### Option: `proxy:` `prx_secret`

MTProxy secret (also supports secrets with dd... and ee... prefixes).

#### Configuration Example

The following is an example yaml configuration.
You must replace `api_id` and `api_hash` with your own values.

```yaml
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

Or, if you enable external port in app settings:

- `http://YOUR-HA:8081` or `http://homeassistant.local:8081`\
Replace *YOUR-HA* with your Home Assistant hostname or IP address.

## Telegram Bot Integration Configuration

This section assumes that you have already set-up the Telegram bot integration.\
If you have not done so, please refer to the [Telegram bot documentation](https://www.home-assistant.io/integrations/telegram_bot).

This configuration requires Home Assistant `2026.2` or later.

To configure your Telegram bot to use your own Telegram bot API server instance (this app), do the following:
1. On your Home Assistant, go to <kbd>Settings</kbd> > <kbd>Devices & services</kbd>.
2. Click on <kbd>Telegram bot</kbd>
3. Click on <kbd>...</kbd> icon of the Telegram bot and press <kbd>Reconfigure</kbd>.
4. Open <kbd>Advanced settings</kbd> section and change <kbd>API endpoint</kbd> to: \
`http://96e39688-telegram-bot-api:8081`
5. Complete the reconfiguration by pressing <kbd>Submit</kbd> several times.

For more details, please refer to the [documentation](https://www.home-assistant.io/integrations/telegram_bot/#configuration).


### Webhook important note
If you use **[webhooks](https://www.home-assistant.io/integrations/telegram_bot/#webhooks)** platform, you should change the webhook `URL` to `http://homeassistant:8123`\
This will ensure direct network interaction between the Telegram Bot API and Home Assistant Core containers.

Currently (HA Core <=  2026.2.*) the integration does not allow you to specify a webhook URL using the `HTTP` protocol.\
Before adopting a [PR](https://github.com/home-assistant/core/pull/162690/) to correct this behavior, this can be done in the following way:

1. Go to <kbd>Settings</kbd> > <kbd>Devices & services</kbd> > <kbd>Telegram bot</kbd>.
2. Click on the <kbd>...</kbd> icon on the top right corner of the page and then Enable debug logging.\
This is used for verifying later.
3. Click on the <kbd>...</kbd> icon beside your bot and then <kbd>Copy entry ID</kbd>.
4. Open the `config/.storage/core.config_entries` file using any editor in SSH or VSCode.
5. Search for the `entry_id` using the value copied in step `3`.
6. You should see a JSON fields named `trusted_networks` and `url`.\
Update the values ​​as follows:
```
"trusted_networks":["149.154.160.0/20","91.108.4.0/22","172.30.33.0/24"]
```
```
"url":"http://homeassistant:8123"
```
7. Restart HA (simply reloading the integration won't work).
8. Check the System logs.\
You should see a entry: `Registering webhook URL: http://homeassistant:8123`.\
This should match what you have updated in step `6`.\
You can also check the webhook URL on the Telegram Bot API statistics page.
9. Disable debug logging.

## ESPHome send message example

```yaml
substitutions:
  # Replace *YOUR-HA* with your Home Assistant hostname or IP address.
  TELEGRAM_API_URL: http://YOUR-HA:8081
  TELEGRAM_BOT_TOKEN: !secret telegram_bot_token
  api_key: !secret api_key
  chat_id: xxxxxxxxx

http_request:
  useragent: esphome/device
  timeout: 5s

button:
  - platform: template
    name: Send Telegram message
    on_press:
      - http_request.post:
          url: "${TELEGRAM_API_URL}/bot${TELEGRAM_BOT_TOKEN}/sendMessage"
          headers:
            Content-Type: application/json
          json:
            chat_id: ${chat_id}
            text: Hello from my ESP Device via local Telegram Bot API server!
          verify_ssl: false
```

## Curl send message example

```bash
#!/bin/bash

# Replace *YOUR-HA* with your Home Assistant hostname or IP address.
API_URL="http://YOUR-HA:8081"

# Replace with your actual API Token and Chat ID
API_TOKEN="<your_api_token>"
CHAT_ID="<your_chat_id>"

# Define the message you want to send
MESSAGE="Hello from my script via local Telegram Bot API server!"

# The curl command to send the message
curl -s -X POST "$API_URL/bot$API_TOKEN/sendMessage" \
    -d chat_id=$CHAT_ID \
    -d text="$MESSAGE" > /dev/null

echo "Message sent!"
```

## FAQs

### Why would I want to use this over the official server `https://api.telegram.org`?

Running your own server has advantages such as larger file size limits for messages and faster response times.\
For more details, please refer to [using a local bot API server](https://core.telegram.org/bots/api#using-a-local-bot-api-server) in the official documentation.\
This app also be helpful in situations where access to Telegram's infrastructure is limited or blocked.\
In this case, you need to set up a connection through a proxy server.

### Can I chat with other users on other Telegram Bot API servers?

Yes, because all Telegram Bot API servers connect to the same set of Telegram MTProto servers.\
Also, the bot's operation through a local API server is no different from its operation through api.telegram.org.\
You continue to use all your automations, scripts, and the rest of the things without any changes.

## Troubleshooting

### Creating an app on my.telegram.org/apps: `ERROR`

This is a fairly common problem, and everyone has their own solution.\
Possible solutions include:

#### Data Formatting
- **App Title and Short Name**: Avoid using the word "Telegram," symbols like @ or #, spaces, or hyphens.\
  Use only Latin characters and numbers. Short name must be between 5 and 32 characters.
- **Random Values**: If meaningful names fail, try entering a random string of letters.\
  You can change these details later; this often helps bypass automated filters.
- **Platform Selection**: Try changing the platform (e.g., select Android or Desktop instead of "Other").

#### Network and Environment
- **Disable VPN/Proxy**: Telegram often blocks API registration from IP addresses it deems suspicious or public.
- **Incognito Mode**: Use your browser's private mode to rule out issues with old cache, cookies, \
  or extensions (especially ad-blockers).
- **Change Network**: Switch from Wi-Fi to mobile data (or vice versa) to get a fresh IP address.

#### Account Status
- **Account Age**: Brand new accounts often face "Error" restrictions.\
  If your account was created recently, wait a few days before trying again.
- **Activity & Premium**: The account must be active.\
  Sometimes having a Telegram Premium subscription helps as it increases the system's trust level.

#### Technical Workarounds
- **Spam Clicking**: Some users report that clicking the "Create application" button repeatedly \
  (sometimes up to 10-20 times) eventually forces the request through.
- **Browser Swap**: If you are using Chrome, try Firefox or Safari.


### Supervisor errors:

`Failed to save: Unknown error, see supervisor logs`

`Failed to to call /addons/96e39688_telegram_bot_api/options/validate -`

`Timeout on /addons/96e39688_telegram_bot_api/options/validate request`

`WARNING (MainThread) [supervisor.utils.pwned] Can't fetch HIBP data: Timeout`

...and so on.

These errors relate to the [Have I Been Pwned (HIBP)](https://haveibeenpwned.com/Passwords) service, which is used by HA to check the passwords you use in apps for leaks.\
If you're having trouble accessing this resource, you may receive these errors.

The workaround is to disable password checking using apps:\
`Terminal & SSH (official)`\
`Advanced SSH & Web Terminal (community)`\
or directly through the `HA OS console`.

You can disable password checking by the pwned service using the command:

**`ha security options --pwned=False`**


And check if this feature is disabled:

```bash
ha sec info
```
Result should be: `pwned: false`

There's an issue on GitHub about this:\
https://github.com/home-assistant/supervisor/issues/6463

Feature description:\
https://www.home-assistant.io/more-info/pwned-passwords/


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
