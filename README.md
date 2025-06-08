
# **Botstruct - Discord Bot Framework**

`Botstruct` is an easy-to-use library for building Discord bots, featuring command and event handling, automatic intent management, and a robust logging system. Setup is quick and straightforward.

## **Installation**

### **With npm**

```bash
npm install botstruct
```

### **With yarn**

```bash
yarn add botstruct
```

---

## **Getting Started**

To begin, create an `App` instance with your configuration:

```typescript
import { GatewayIntentBits } from "discord.js";
import { App } from "botstruct";

const client = new App({
    intents: [YOUR_INTENTS_HERE], // Example: [GatewayIntentBits.Guilds]
});

client.login("YOUR_BOT_TOKEN");  // Start the bot with your token
```

---

## **Defining a Command with Botstruct**

Commands are simple to set up! Here’s a `/ping` command that replies with "Pong!":

```typescript
import { CommandInteraction, SlashCommandBuilder } from "discord.js";
import { NewCommand } from "botstruct";

export default NewCommand({
    data: new SlashCommandBuilder().setName("ping").setDescription("Ping pong!"),
    execute: async (interaction) => {
        await interaction.reply("Pong!");  // Sends a reply to the user
    },
});
```

## **Handling Events with Botstruct**

Events let your bot react to Discord activity. Here’s how to respond to messages using the `messageCreate` event:

```typescript
import { Message } from "discord.js";
import { NewEvent } from "botstruct";

export default NewEvent({
    name: "messageCreate",  // Event name
    execute(...args) {
        const message = args[0] as Message;  // Incoming message

        if (message.author.bot) return;  // Ignore bot messages
        
        if (message.content === "!ping") {  // If the message is "!ping"
            message.reply("Pong!");  // Reply with "Pong!"
        }
    },
});
```

---

## **Features**

- **Commands & Subcommands**: Build simple or advanced commands, with or without subcommands.
- **Automatic Intent Management**: Required intents are enabled for you.
- **Event Handling**: Listen to Discord events and respond as needed.
- **Logger**: Clear, colorful logging for messages, errors, and info.

---

## **By ddnrz 🔨**


