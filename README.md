# Discord-chat-bot
import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True  # To enable reading message content

bot = commands.Bot(command_prefix='!', intents=intents)

# When the bot is ready and logged in
@bot.event
async def on_ready():
    print(f'Yo! Bot ready as {bot.user}')

# When a message is received
@bot.event
async def on_message(message):
    if message.author == bot.user:
        return  # Ignore messages from itself
    
    msg = message.content.lower()

    # Hinglish slang responses
    if 'hello' in msg or 'hi' in msg:
        await message.channel.send('Oye, kya haal hai? Bindaas? 😎')
    elif 'kya haal hai' in msg or 'kaise ho' in msg:
        await message.channel.send('Mast bro! Tere kya scene hai?')
    elif 'chalo baat karte hain' in msg or 'baat kar' in msg:
        await message.channel.send('Bata bhai, kya chal raha hai zindagi mein?')
    elif 'bye' in msg or 'chalte hain' in msg:
        await message.channel.send('Thik hai, milte hain phir! Apna dhyan rakh. ✌️')
    else:
        # Optional: generic slang reply if message doesn't match
        await message.channel.send('Woh kya baat hui yaar, thoda clear bol! 😜')

    # Process commands if you add any in the future
    await bot.process_commands(message)

# Paste your bot token here (keep it secret)
bot.run('YOUR_BOT_TOKEN_HERE')
