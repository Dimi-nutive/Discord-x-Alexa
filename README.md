# Summer 2021 - Replit Hackathon / Alexa skill

## Unofficial Discord API - Alexa Skill

Send instructions to your Discord account with this skill.

### Why Discord ?

I don't know. :)

## Intents

- [x] `GetLastMention`: Tells who mentionned you the last time.
- [x] `LastMentionMarkAsRead`: Mark as read the latest mention you've got.
- [x] `CreateMessage`: Send a message to a user or a guild text channel mentionned in the aliases.json file.

These are basic intents but I'll add more !

## Installation

Clone this repository and run `yarn` to install depedencies.

Then you can run `yarn start` to start the webserver, or
`yarn start:watch` if you prefer use nodemon.

### Create skill

You can follow [this tutorial/template from Replit](https://blog.replit.com/replexa)
to create your Alexa skill, and replace their repository by mine.
Copy `.env.sample` to `.env`, give [your account Discord token](https://gist.github.com/Vexcited/94b9691653195d6ce3b9df6bc8dabe0f),
give your Alexa Skill ID then point the skill endpoint to your repl URL,
import intents and enjoy.

### Intents and languages

This skill **supports French, English and Spanish (BETA)**.
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
    "my server global channel": "837076888744755321"
  },
  "users": {
    "my friend": "590848440922144788"
  }
}
```

## Skill Invocation / Commands

### English

Invocation name: `unofficial discord a. p. i.`. \
So you would say something like, `Alexa, open unofficial discord` or `Alexa, open discord api skill`.

#### Send a message

- `Send a message`, or `Send a message to a user|channel` to shortcut the first parameter.
  Then you'll be asked for user|channel alias, then for the message content.

#### Read and mark last received mention/ping as read

- `Get my last mention|ping` to read the latest mention you received.
- `Mark as read my last mention` or `Clear last mention` to mark as read the latest mention you received.

### French

Nom d'invocation: `a. p. i. discord non officielle` \
Vous pourrez dire un truc du style, `Alexa, ouvre la skill discord non officiel`.

#### Envoyer un message

- `Envoie un message`, ou `Envoie un message à un utilisateur|salon` pour éviter de préciser le
  premier paramètre. Il vous sera demandé l'alias de l'utilisateur|du salon, et ensuite le contenu du message.

#### Lire et marquer la dernière mention reçue comme lue

- `Lis ma dernière mention|mon dernier ping reçu(e)` pour lire la dernière mention/dernier ping reçu.
- `Efface la dernière mention` ou `Marque la dernière mention/le dernier ping reçu comme lu(e)` pour marquer comme lu le dernier ping/dernière mention reçu(e).

### Spanish

Nombre invocatorio: `API no oficial de discord` (pronunciar API por letras) \
Por lo que dirias algo como: `Alexa, abre API no oficial de discord`.

#### Enviar un mensaje

- `Enviar un mensaje`, o `Enviar un mensaje a un usuario|canal` para evitar indicar el primer parametro. Despues le perguntaran por un alias de un usuario|canal, y despues el contenido del mensaje.

#### Leer y marcar como leido la ultima mencion/ping como leido

- `Obten mi ultima mención` o `Obten mi ultimo ping` para que Alexa te lea la ultima mención que recibió.
- `Marca como leido mi ultima|ultimo mención|ping` o `Eliminar mi ultima|o mención|ping`

## Contribute ?

You can contribute if you want ! Everything is in `/src`.
