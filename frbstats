import discord
import os
import requests

prefix="$"
client = discord.Client()

@client.event
async def on_ready():
    print('We have logged in as {0.user}'.format(client))
    await client.change_presence(activity=discord.Activity(type=discord.ActivityType.watching, name="the sky"))

@client.event
async def on_message(message):
    if message.author == client.user:
        return

    if message.content.startswith(prefix+'hello'):
        await message.channel.send('Hello!')
    
    if message.content.startswith(prefix+'frb'):
        frb=message.content.split(" ")[1]
        response = requests.get("https://www.herta-experiment.org/frbstats/api/search?frb=" + frb)
        if response.status_code == 200:
            await message.channel.send(response.json())

client.run("TOKEN")
