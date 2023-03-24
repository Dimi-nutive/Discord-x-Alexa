# Discord x Alexa

## A Discord API | Alexa Skill

Alexa fetches your command | interprets and then perform an action on your discord.


## Intents

- [x] `GetLastMention`: Tells you about your recent mention
- [x] `LastMentionMarkAsRead`: Mark as read the latest mention you've got.
- [x] `CreateMessage`: Send a message to a user or a guild text channel mentionned in the aliases.json file.

| || | || | BETA VERSION 0.1

These are basic intents but I'll add more !

## Installation

Clone this repository and run `yarn` to install depedencies.

Then you can run `yarn start` to start the webserver, or
`yarn start:watch` if you prefer use nodemon.

### Create skill

In `.env`, give your account Discord token,
give your Alexa Skill ID then point the skill endpoint to your repl URL,
import intents and enjoy.

### Intents and languages

To import them, go to Assets -> JSON Editor in Alexa,
go to the `/intents` folder, and import
the JSON file that you want to Alexa.

## Aliases

An alias system is provided to make friends/channels name more easier to say.

**When you need to provide a friend/channel name, you'll need to provide the alias name that you given, not the name written in Discord. Otherwise, it will not recognize it because Alexa will only search the name in the aliases file.**

### Create aliases file

Copy `/aliases.sample.json` to `/aliases.json` and edit it.

### Structure

It contains two parts (for the moment): `"channels", "users"`.

In these parts you can give to a _thing_, an alias like this `"alias name": "ThingSnowflakeId"`.

The most important thing is that the alias name **MUST** be **in lower case**.
The another most important thing is for IDs. `users` IDs must be the User ID, not the Channel ID.
For `channels`, you can give the Channel ID.

> To get the User/Channel ID, first, make sure you have "Developer Mode" activated in your paramaters, then just right click on the user/channel, and click "Copy ID". On mobile, keep your finger on the channel/user and you'll see a menu, then click "Copy ID".

### Example

_You want to get access a text channel in a guild and a private DM with a friend._

```json
{
  "channels": {
    "test-server": "1088722421969862692"
  },
  "users": {
    "test": "590848440922144788"
  }
}
```

## Skill Invocation / Commands


Invocation name: `unofficial discord a. p. i.`. \
So you would say something like, `Alexa, open unofficial discord` or `Alexa, open discord api skill`.

#### Send a message

- `Send a message`, or `Send a message to a user|channel` to shortcut the first parameter.
  Then you'll be asked for user|channel alias, then for the message content.

#### Read and mark last received mention/ping as read

- `Get my last mention|ping` to read the latest mention you received.
- `Mark as read my last mention` or `Clear last mention` to mark as read the latest mention you received.

