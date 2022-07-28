discorder
==========

.. image:: https://media.discordapp.net/attachments/978777405621674024/997511466427105310/lv_0_20220707215402.gif
   :target: https://discord.gg/bGrtrxnWKj
   :alt:  Discord сервер
.. image:: https://img.shields.io/pypi/v/discord.py.svg
   :target: https://pypi.python.org/pypi/discord.py
   :alt: PyPI version info
.. image:: https://img.shields.io/pypi/pyversions/discord.py.svg
   :target: https://pypi.python.org/pypi/discord.py
   :alt: PyPI supported Python versions

Библиотка для написания discord ботов


Установка 
----------

**Python 3.8 и выше**


.. code:: sh
    pip install discord 
    





To install the development version, do the following:

.. code:: sh

    $ cd discorder
    $ python3 -m pip install discorder


Дополнительные пакеты
~~~~~~~~~~~~~~~~~~

* `PyNaCl <https://pypi.org/project/PyNaCl/>`__ (для голосовой активности)


Self бот
--------------

.. code:: py

    import discord

    class MyClient(discord.Client):
        async def on_ready(self):
            print('Logged on as', self.user)

        async def on_message(self, message):
            # don't respond to ourselves
            if message.author == self.user:
                return

            if message.content == 'ping':
                await message.channel.send('pong')

    intents = discord.Intents.default()
    intents.message_content = True
    client = MyClient(intents=intents)
    client.run('token')

Пример  бота
~~~~~~~~~~~~~

.. code:: py

    import discord
    from discord.ext import commands

    intents = discord.Intents.default()
    intents.message_content = True
    bot = commands.Bot(command_prefix='>', intents=intents)

    @bot.command()
    async def ping(ctx):
        await ctx.send('pong')

    bot.run('token')



Ссылки
------

- `Documentation <https://discordpy.readthedocs.io/en/latest/index.html>`_
- `Discord API <https://discord.gg/discord-api>`_
