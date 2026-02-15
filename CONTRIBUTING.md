# Contributing

## Development

1. Create a fork of this repository `https://github.com/avbor/hassio-apps`.
2. Clone your fork.
3. Open the project with VSCode.
4. Open the command palette (<kbd>Ctrl+Shift+P</kbd> for Windows) and select <kbd>Dev Containers: Rebuild and Reopen in Container</kbd>.
5. Click on the search bar and select <kbd>Run Task</kbd>, then choose the <kbd>Start Home Assistant</kbd>task. Give it a while for it to download and start up.
6. Open a new terminal: Go to <kbd>Terminal</kbd> > <kbd>New Terminal</kbd>.
7. Install the app by running the following in the terminal: <kbd>ha addons install local_telegram_bot_api</kbd>.
8. Configure the app by updating `api_id` and `api_hash` with your values. Refer to `DOCS.md` on how to obtain these values.
9. Click on the search bar, select <kbd>Run Task</kbd>, then choose the <kbd>Start Addon</kbd>task then choose the <kbd>telegram_bot_api</kbd> slug.
10. To verify the app is running properly, run the following in the terminal (replace *YourBotToken* accordingly): `curl http://localhost:8081/bot<YourBotToken>/getMe`.

## Useful Links

Creating a new app app tutorial: https://developers.home-assistant.io/docs/add-ons/tutorial
