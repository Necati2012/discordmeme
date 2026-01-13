import discord
from discord.ext import commands
import random
import os
TOKEN = 'token buraya'
intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='!', intents=intents)
@bot.event
async def on_ready():
    print(f'{bot.user} giriş yaptı!')
@bot.command()
async def meme(ctx):
    images = [f for f in os.listdir('images') if f.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.webp'))]
    if images:
        await ctx.send(file=discord.File(f'images/{random.choice(images)}'))
    else:
        await ctx.send('Görsel bulunamadı!')
bot.run(TOKEN)
