# tg2twi
Telegram to Twitter Bot

This repository contains a Python script that integrates a Telegram bot with Twitter. The bot listens for new messages in a specific Telegram channel and posts them to a connected Twitter account. It uses polling with retry logic for resilience against network issues.

Features
 • Telegram to Twitter Integration: Automatically posts messages from a Telegram channel to Twitter.
 • Retry Logic: Ensures resilience by retrying network requests with exponential backoff.
 • Logging: Logs errors and critical events for monitoring and debugging.
 • Graceful Shutdown: Handles interruptions (e.g., Ctrl+C) gracefully.

Requirements
 • Python 3.10 or later
 • Telegram bot token
 • Twitter API keys and tokens
 
1. Set up a .env file with the following variables:
```
TELEGRAM_TOKEN=your_telegram_bot_token
TWITTER_CONSUMER_KEY=your_twitter_consumer_key
TWITTER_CONSUMER_SECRET=your_twitter_consumer_secret
TWITTER_ACCESS_TOKEN=your_twitter_access_token
TWITTER_ACCESS_TOKEN_SECRET=your_twitter_access_token_secret
CHANNEL_USERNAME=your_channel_username_without_@
```
Usage

 1. Run the bot:
```
python tg2twi.py
```

 2. Ensure your Telegram bot is added to the channel with appropriate admin permissions.

How It Works
 1. The bot uses polling to fetch new messages from the Telegram channel.
 2. Messages are processed and posted to Twitter via the Twitter API.
 3. Retry logic is implemented using the tenacity library to handle transient errors.

Configuration
 • Polling Interval: Adjust the poll_interval in application.run_polling for how frequently the bot checks for updates.
 • Max Retry Attempts: Modify stop_after_attempt in get_updates_with_retry to change the number of retries for network requests.

Dependencies
```
 • python-telegram-bot
 • tenacity
 • httpx
```

Install dependencies with:
```
pip install python-telegram-bot tenacity python-dotenv httpx
```

Logging
Logs are written to the console with timestamps and severity levels. You can redirect these to a file by modifying the logging.basicConfig configuration.

Contributing
Contributions are welcome! Feel free to submit pull requests or open issues for bugs and feature requests.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Troubleshooting
Common Errors
 • NetworkError: Server disconnected without sending a response:
 • Check your internet connection.
 • Ensure Telegram servers are reachable.
 • The retry logic in the script should handle temporary outages.
 • Twitter Posting Issues:
 • Verify your Twitter API keys and permissions.

For more help, open an issue in this repository.
