# Telegram Copy Bot

A lightweight Telegram copy bot focused on reliable message copying from one chat to another.

## What it does
This bot copies (not forward) messages from a source channel (which doesn't have administrator privileges on it) to a destination chat (simple user, channel, etc.).

## Customization
This project is intentionally kept simple and focused. If you need extra behavior (for example editing copied messages, handling updates differently, or adding filters), you can customize the bot for your own workflow.

To customize confidently:
- Review the implementation in `app/main.py` to understand the current message handling flow.
- Refer to [python-telegram](http://python-telegram.readthedocs.io/) for client usage patterns.
- Refer to [TDLib documentation](https://core.telegram.org/tdlib/docs/) for protocol-level capabilities and limits.

## How to use
1. Copy `.env.example` to `.env`.
    ```
    cp .env.example .env
    ```
2. Obtain `api_id` and `api_hash` from [this link](https://my.telegram.org/apps) and fill it inside `Telegram Configuration` section of the `.env` file alongside other configurations (such as phone number of your user, which acts as your bot).
3. Run the project via Docker and login to Telegram:
    ```
    docker run -it \
        --env-file=.env \
        -v td-data:/tmp/.tdlib_files \
        radinshayanfar/tgcopybot
    ```
4. After logging in, you will see your chat names and their chat id. Copy chat ids of source and destination chats and put them inside `App Configuration` section of the `.env` file.
5. Run the container in detached mode and it will do the job:
     ```
     docker run -d \
        --env-file=.env \
        -v td-data:/tmp/.tdlib_files \
        radinshayanfar/tgcopybot
    ```
