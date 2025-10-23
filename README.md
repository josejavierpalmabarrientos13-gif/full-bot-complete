import discord
from discord.ext import commands
import requests
import random
import asyncio
import Jose
import os

intents = discord.Intents.default()
intents.message_content = True
intents.members = True  

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.command()
async def hello(ctx):
    await ctx.send(f'Hola, soy un bot este es mi num: Jose +502 4094 5317{bot.user}!')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)

@bot.command()
async def moneda(ctx):
    await ctx.send(random.choice(["Cara", "Escudo"]))


@bot.command()
async def edad(ctx,year:int):
    await ctx.send(f"tu edad es {2025-year}")
@bot.command()
async def meme(ctx):
    with open('cheemsmemes/cheemsmemes.png', 'rb') as f:
        memes = discord.File(f)
    await ctx.send(file = memes)
@bot.command() 
async def recordar(ctx), tiempo: int, *, texto: str): 
    await ctx.send(f"⏳ Te recordaré esto en {tiempo}, segundos: {texto}")  
@bot.command()
async def bienvenida(ctx):
    await ctx.send(f"🎉 ¡Bienvenido/a {ctx.author.mention} al servidor! Esperamos que la pases increíble 💫")   
@perfil.command()
async def setbio(ctx, *, texto: str):
 
    bios = load_bios()
    bios[str(ctx.author.id)] = texto
    save_bios(bios)
    await ctx.send(f"✅ Tu biografía ha sido guardada:\n> {texto}")
@bot.command()
async def ranking(ctx):
    xp_data = load_xp()
    if not xp_data:
        await ctx.send("⚠️ Aún no hay datos de XP en el servidor.")
        return
    
    sorted_xp = sorted(xp_data.items(), key=lambda x: x[1], reverse=True)
    msg = "🏆 **Ranking del servidor** 🏆\n\n"
    
    for i, (user_id, xp) in enumerate(sorted_xp[:10], start=1):
        user = await bot.fetch_user(int(user_id))
        msg += f"{i}. {user.name} — {xp} XP\n"
    
    await ctx.send(msg)
bot.run("MTQyMzExNTY1MzUzNDk3ODE5OQ.G9hzpH.cHu3EPyhw3I5Iz0_4Bgb_mX6LpE83m11zimhz4") 


