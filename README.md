
# Discord Gmail Keyword Notifier

The `discord-gmail-keyword-notifier` is a Python script designed to monitor your Gmail inbox for emails from specific senders and containing certain keywords. When a matching email is detected, the script sends a detailed, formatted notification to a Discord webhook with relevant information such as the sender, recipient, and subject.

## Features

- **Monitors Gmail for specific keywords and senders.**
- **Sends a detailed notification to a Discord webhook when a matching email is found.**
- **Customizable sender list, keywords, and recipient exclusion list.**
- **Easy to configure via a JSON file.**

## Requirements

- **Python 3.x**
- **Gmail account with IMAP access enabled.**
- **Discord webhook URL.**

### Python Libraries

Ensure the following Python libraries are installed:

```bash
pip install imaplib2 email requests
```

## Setup Instructions

### 1. Clone or Download the Repository

Clone the repository or download the script files:

```bash
git clone https://github.com/Nukewire/discord-gmail-keyword-notifier.git
cd discord-gmail-keyword-notifier
```

### 2. Enable IMAP for Your Gmail Account

To allow the script to access your Gmail account, enable IMAP access:

- Go to your [Gmail settings](https://mail.google.com/mail/u/0/#settings/fwdandpop).
- Under "Forwarding and POP/IMAP," enable IMAP.

### 3. Create an App Password (Optional but Recommended)

For security reasons, it's recommended to use an [App Password](https://support.google.com/mail/answer/185833?hl=en) instead of your regular Gmail password.

### 4. Configure the Script

Edit the `config.json` file to match your requirements:

```json
{
    "imap_server": "imap.gmail.com",
    "imap_user": "your_email@gmail.com",
    "imap_password": "your_password_or_app_password",
    "webhook_url": "https://discord.com/api/webhooks/your_webhook_url",
    "email_senders": ["example.com"],
    "keywords": ["important", "urgent", "project"],
    "check_interval_seconds": 300,
    "recipient_exclude_list": ["exclude_this@example.com", "another_exclude@example.com"]
}
```

### 5. Run the Script

Run the script using Python:

```bash
python discord-gmail-keyword-notifier.py
```

### 6. Log Files

- **`email_check_search.log`**: Standard logs, including connection status and general information.
- **`email_verbose_search.log`**: Detailed logs for debugging, including email content and processing steps.

## Configuration Options

### `imap_server`
- **Description**: The IMAP server address.
- **Default**: `imap.gmail.com`

### `imap_user`
- **Description**: Your Gmail email address.

### `imap_password`
- **Description**: Your Gmail password or app-specific password.

### `webhook_url`
- **Description**: The Discord webhook URL where notifications will be sent.

### `email_senders`
- **Description**: A list of email senders to monitor.

### `keywords`
- **Description**: A list of keywords to search for in the email subject and body.

### `check_interval_seconds`
- **Description**: Time interval (in seconds) between checks.
- **Default**: `300` (5 minutes)

### `recipient_exclude_list`
- **Description**: A list of recipient email addresses to exclude from notifications.

## How It Works

1. The script connects to your Gmail inbox via IMAP.
2. It searches for emails from specified senders and containing specified keywords.
3. If an email matches the criteria, a notification is sent to the Discord webhook.
4. The script runs continuously, checking for new emails at the specified interval.

## Troubleshooting

- **IMAP Connection Issues**: Ensure IMAP is enabled for your Gmail account and that you’re using an app-specific password if two-factor authentication is enabled.
- **No Notifications**: Verify that the script is running and that the `email_senders`, `keywords`, and `recipient_exclude_list` are correctly configured.
- **Debugging**: Check the `email_verbose_search.log` file for detailed information on each processed email.

## Contributing

If you’d like to contribute to this project, feel free to submit a pull request or open an issue on [GitHub](https://github.com/yourusername/discord-gmail-keyword-notifier).

## License

This project is licensed under the MIT License.

---

### Additional Notes:
- Ensure that the config file (`config.json`) is correctly formatted and located in the same directory as the script.
- Regularly check the log files for any errors or issues that may arise during operation.

---

