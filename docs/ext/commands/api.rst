.. currentmodule:: hcord

API Reference
===============

The following section outlines the API of hcord's command extension module.

.. _ext_commands_api_bot:

Bots
------

Bot
~~~~

.. attributetable:: hcord.ext.commands.Bot

.. autoclass:: hcord.ext.commands.Bot
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, check, check_once, command, event, group, listen

    .. automethod:: Bot.after_invoke()
        :decorator:

    .. automethod:: Bot.before_invoke()
        :decorator:

    .. automethod:: Bot.check()
        :decorator:

    .. automethod:: Bot.check_once()
        :decorator:

    .. automethod:: Bot.command(*args, **kwargs)
        :decorator:
    
    .. automethod:: Bot.event()
        :decorator:

    .. automethod:: Bot.group(*args, **kwargs)
        :decorator:

    .. automethod:: Bot.listen(name=None)
        :decorator:

AutoShardedBot
~~~~~~~~~~~~~~~~

.. attributetable:: hcord.ext.commands.AutoShardedBot

.. autoclass:: hcord.ext.commands.AutoShardedBot
    :members:

Prefix Helpers
----------------

.. autofunction:: hcord.ext.commands.when_mentioned

.. autofunction:: hcord.ext.commands.when_mentioned_or

.. _ext_commands_api_events:

Event Reference
-----------------

These events function similar to :ref:`the regular events <hcord-api-events>`, except they
are custom to the command extension module.

.. function:: hcord.ext.commands.on_command_error(ctx, error)

    An error handler that is called when an error is raised
    inside a command either through user input error, check
    failure, or an error in your own code.

    A default one is provided (:meth:`.Bot.on_command_error`).

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`
    :param error: The error that was raised.
    :type error: :class:`.CommandError` derived

.. function:: hcord.ext.commands.on_command(ctx)

    An event that is called when a command is found and is about to be invoked.

    This event is called regardless of whether the command itself succeeds via
    error or completes.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. function:: hcord.ext.commands.on_command_completion(ctx)

    An event that is called when a command has completed its invocation.

    This event is called only if the command succeeded, i.e. all checks have
    passed and the user input it correctly.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. _ext_commands_api_command:

Commands
----------

Decorators
~~~~~~~~~~~~

.. autofunction:: hcord.ext.commands.command
    :decorator:

.. autofunction:: hcord.ext.commands.group
    :decorator:

Command
~~~~~~~~~

.. attributetable:: hcord.ext.commands.Command

.. autoclass:: hcord.ext.commands.Command
    :members:
    :special-members: __call__
    :exclude-members: after_invoke, before_invoke, error

    .. automethod:: Command.after_invoke()
        :decorator:

    .. automethod:: Command.before_invoke()
        :decorator:

    .. automethod:: Command.error()
        :decorator:

Group
~~~~~~

.. attributetable:: hcord.ext.commands.Group

.. autoclass:: hcord.ext.commands.Group
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, command, error, group

    .. automethod:: Group.after_invoke()
        :decorator:

    .. automethod:: Group.before_invoke()
        :decorator:

    .. automethod:: Group.command(*args, **kwargs)
        :decorator:

    .. automethod:: Group.error()
        :decorator:

    .. automethod:: Group.group(*args, **kwargs)
        :decorator:

GroupMixin
~~~~~~~~~~~

.. attributetable:: hcord.ext.commands.GroupMixin

.. autoclass:: hcord.ext.commands.GroupMixin
    :members:
    :exclude-members: command, group

    .. automethod:: GroupMixin.command(*args, **kwargs)
        :decorator:

    .. automethod:: GroupMixin.group(*args, **kwargs)
        :decorator:

.. _ext_commands_api_cogs:

Cogs
------

Cog
~~~~

.. attributetable:: hcord.ext.commands.Cog

.. autoclass:: hcord.ext.commands.Cog
    :members:

CogMeta
~~~~~~~~

.. attributetable:: hcord.ext.commands.CogMeta

.. autoclass:: hcord.ext.commands.CogMeta
    :members:

.. _ext_commands_help_command:

Help Commands
---------------

HelpCommand
~~~~~~~~~~~~

.. attributetable:: hcord.ext.commands.HelpCommand

.. autoclass:: hcord.ext.commands.HelpCommand
    :members:

DefaultHelpCommand
~~~~~~~~~~~~~~~~~~~

.. attributetable:: hcord.ext.commands.DefaultHelpCommand

.. autoclass:: hcord.ext.commands.DefaultHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

MinimalHelpCommand
~~~~~~~~~~~~~~~~~~~

.. attributetable:: hcord.ext.commands.MinimalHelpCommand

.. autoclass:: hcord.ext.commands.MinimalHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

Paginator
~~~~~~~~~~

.. attributetable:: hcord.ext.commands.Paginator

.. autoclass:: hcord.ext.commands.Paginator
    :members:

Enums
------

.. class:: BucketType
    :module: hcord.ext.commands

    Specifies a type of bucket for, e.g. a cooldown.

    .. attribute:: default

        The default bucket operates on a global basis.
    .. attribute:: user

        The user bucket operates on a per-user basis.
    .. attribute:: guild

        The guild bucket operates on a per-guild basis.
    .. attribute:: channel

        The channel bucket operates on a per-channel basis.
    .. attribute:: member

        The member bucket operates on a per-member basis.
    .. attribute:: category

        The category bucket operates on a per-category basis.
    .. attribute:: role

        The role bucket operates on a per-role basis.

        .. versionadded:: 1.3


.. _ext_commands_api_checks:

Checks
-------

.. autofunction:: hcord.ext.commands.check(predicate)
    :decorator:

.. autofunction:: hcord.ext.commands.check_any(*checks)
    :decorator:

.. autofunction:: hcord.ext.commands.has_role(item)
    :decorator:

.. autofunction:: hcord.ext.commands.has_permissions(**perms)
    :decorator:

.. autofunction:: hcord.ext.commands.has_guild_permissions(**perms)
    :decorator:

.. autofunction:: hcord.ext.commands.has_any_role(*items)
    :decorator:

.. autofunction:: hcord.ext.commands.bot_has_role(item)
    :decorator:

.. autofunction:: hcord.ext.commands.bot_has_permissions(**perms)
    :decorator:

.. autofunction:: hcord.ext.commands.bot_has_guild_permissions(**perms)
    :decorator:

.. autofunction:: hcord.ext.commands.bot_has_any_role(*items)
    :decorator:

.. autofunction:: hcord.ext.commands.cooldown(rate, per, type=hcord.ext.commands.BucketType.default)
    :decorator:

.. autofunction:: hcord.ext.commands.dynamic_cooldown(cooldown, type=BucketType.default)
    :decorator:

.. autofunction:: hcord.ext.commands.max_concurrency(number, per=hcord.ext.commands.BucketType.default, *, wait=False)
    :decorator:

.. autofunction:: hcord.ext.commands.before_invoke(coro)
    :decorator:

.. autofunction:: hcord.ext.commands.after_invoke(coro)
    :decorator:

.. autofunction:: hcord.ext.commands.guild_only(,)
    :decorator:

.. autofunction:: hcord.ext.commands.dm_only(,)
    :decorator:

.. autofunction:: hcord.ext.commands.is_owner(,)
    :decorator:

.. autofunction:: hcord.ext.commands.is_nsfw(,)
    :decorator:

.. _ext_commands_api_context:

Cooldown
---------

.. attributetable:: hcord.ext.commands.Cooldown

.. autoclass:: hcord.ext.commands.Cooldown
    :members:

Context
--------

.. attributetable:: hcord.ext.commands.Context

.. autoclass:: hcord.ext.commands.Context
    :members:
    :inherited-members:
    :exclude-members: history, typing

    .. automethod:: hcord.ext.commands.Context.history
        :async-for:

    .. automethod:: hcord.ext.commands.Context.typing
        :async-with:

.. _ext_commands_api_converters:

Converters
------------

.. autoclass:: hcord.ext.commands.Converter
    :members:

.. autoclass:: hcord.ext.commands.ObjectConverter
    :members:

.. autoclass:: hcord.ext.commands.MemberConverter
    :members:

.. autoclass:: hcord.ext.commands.UserConverter
    :members:

.. autoclass:: hcord.ext.commands.MessageConverter
    :members:

.. autoclass:: hcord.ext.commands.PartialMessageConverter
    :members:

.. autoclass:: hcord.ext.commands.GuildChannelConverter
    :members:

.. autoclass:: hcord.ext.commands.TextChannelConverter
    :members:

.. autoclass:: hcord.ext.commands.VoiceChannelConverter
    :members:

.. autoclass:: hcord.ext.commands.StoreChannelConverter
    :members:

.. autoclass:: hcord.ext.commands.StageChannelConverter
    :members:

.. autoclass:: hcord.ext.commands.CategoryChannelConverter
    :members:

.. autoclass:: hcord.ext.commands.InviteConverter
    :members:

.. autoclass:: hcord.ext.commands.GuildConverter
    :members:

.. autoclass:: hcord.ext.commands.RoleConverter
    :members:

.. autoclass:: hcord.ext.commands.GameConverter
    :members:

.. autoclass:: hcord.ext.commands.ColourConverter
    :members:

.. autoclass:: hcord.ext.commands.EmojiConverter
    :members:

.. autoclass:: hcord.ext.commands.PartialEmojiConverter
    :members:

.. autoclass:: hcord.ext.commands.ThreadConverter
    :members:

.. autoclass:: hcord.ext.commands.GuildStickerConverter
    :members:

.. autoclass:: hcord.ext.commands.clean_content
    :members:

.. autoclass:: hcord.ext.commands.Greedy()

.. autofunction:: hcord.ext.commands.run_converters

Flag Converter
~~~~~~~~~~~~~~~

.. autoclass:: hcord.ext.commands.FlagConverter
    :members:

.. autoclass:: hcord.ext.commands.Flag()
    :members:

.. autofunction:: hcord.ext.commands.flag

.. _ext_commands_api_errors:

Exceptions
-----------

.. autoexception:: hcord.ext.commands.CommandError
    :members:

.. autoexception:: hcord.ext.commands.ConversionError
    :members:

.. autoexception:: hcord.ext.commands.MissingRequiredArgument
    :members:

.. autoexception:: hcord.ext.commands.ArgumentParsingError
    :members:

.. autoexception:: hcord.ext.commands.UnexpectedQuoteError
    :members:

.. autoexception:: hcord.ext.commands.InvalidEndOfQuotedStringError
    :members:

.. autoexception:: hcord.ext.commands.ExpectedClosingQuoteError
    :members:

.. autoexception:: hcord.ext.commands.BadArgument
    :members:

.. autoexception:: hcord.ext.commands.BadUnionArgument
    :members:

.. autoexception:: hcord.ext.commands.BadLiteralArgument
    :members:

.. autoexception:: hcord.ext.commands.PrivateMessageOnly
    :members:

.. autoexception:: hcord.ext.commands.NoPrivateMessage
    :members:

.. autoexception:: hcord.ext.commands.CheckFailure
    :members:

.. autoexception:: hcord.ext.commands.CheckAnyFailure
    :members:

.. autoexception:: hcord.ext.commands.CommandNotFound
    :members:

.. autoexception:: hcord.ext.commands.DisabledCommand
    :members:

.. autoexception:: hcord.ext.commands.CommandInvokeError
    :members:

.. autoexception:: hcord.ext.commands.TooManyArguments
    :members:

.. autoexception:: hcord.ext.commands.UserInputError
    :members:

.. autoexception:: hcord.ext.commands.CommandOnCooldown
    :members:

.. autoexception:: hcord.ext.commands.MaxConcurrencyReached
    :members:

.. autoexception:: hcord.ext.commands.NotOwner
    :members:

.. autoexception:: hcord.ext.commands.MessageNotFound
    :members:

.. autoexception:: hcord.ext.commands.MemberNotFound
    :members:

.. autoexception:: hcord.ext.commands.GuildNotFound
    :members:

.. autoexception:: hcord.ext.commands.UserNotFound
    :members:

.. autoexception:: hcord.ext.commands.ChannelNotFound
    :members:

.. autoexception:: hcord.ext.commands.ChannelNotReadable
    :members:

.. autoexception:: hcord.ext.commands.ThreadNotFound
    :members:

.. autoexception:: hcord.ext.commands.BadColourArgument
    :members:

.. autoexception:: hcord.ext.commands.RoleNotFound
    :members:

.. autoexception:: hcord.ext.commands.BadInviteArgument
    :members:

.. autoexception:: hcord.ext.commands.EmojiNotFound
    :members:

.. autoexception:: hcord.ext.commands.PartialEmojiConversionFailure
    :members:

.. autoexception:: hcord.ext.commands.GuildStickerNotFound
    :members:

.. autoexception:: hcord.ext.commands.BadBoolArgument
    :members:

.. autoexception:: hcord.ext.commands.MissingPermissions
    :members:

.. autoexception:: hcord.ext.commands.BotMissingPermissions
    :members:

.. autoexception:: hcord.ext.commands.MissingRole
    :members:

.. autoexception:: hcord.ext.commands.BotMissingRole
    :members:

.. autoexception:: hcord.ext.commands.MissingAnyRole
    :members:

.. autoexception:: hcord.ext.commands.BotMissingAnyRole
    :members:

.. autoexception:: hcord.ext.commands.NSFWChannelRequired
    :members:

.. autoexception:: hcord.ext.commands.FlagError
    :members:

.. autoexception:: hcord.ext.commands.BadFlagArgument
    :members:

.. autoexception:: hcord.ext.commands.MissingFlagArgument
    :members:

.. autoexception:: hcord.ext.commands.TooManyFlags
    :members:

.. autoexception:: hcord.ext.commands.MissingRequiredFlag
    :members:

.. autoexception:: hcord.ext.commands.ExtensionError
    :members:

.. autoexception:: hcord.ext.commands.ExtensionAlreadyLoaded
    :members:

.. autoexception:: hcord.ext.commands.ExtensionNotLoaded
    :members:

.. autoexception:: hcord.ext.commands.NoEntryPointError
    :members:

.. autoexception:: hcord.ext.commands.ExtensionFailed
    :members:

.. autoexception:: hcord.ext.commands.ExtensionNotFound
    :members:

.. autoexception:: hcord.ext.commands.CommandRegistrationError
    :members:


Exception Hierarchy
~~~~~~~~~~~~~~~~~~~~~

.. exception_hierarchy::

    - :exc:`~.hcordException`
        - :exc:`~.commands.CommandError`
            - :exc:`~.commands.ConversionError`
            - :exc:`~.commands.UserInputError`
                - :exc:`~.commands.MissingRequiredArgument`
                - :exc:`~.commands.TooManyArguments`
                - :exc:`~.commands.BadArgument`
                    - :exc:`~.commands.MessageNotFound`
                    - :exc:`~.commands.MemberNotFound`
                    - :exc:`~.commands.GuildNotFound`
                    - :exc:`~.commands.UserNotFound`
                    - :exc:`~.commands.ChannelNotFound`
                    - :exc:`~.commands.ChannelNotReadable`
                    - :exc:`~.commands.BadColourArgument`
                    - :exc:`~.commands.RoleNotFound`
                    - :exc:`~.commands.BadInviteArgument`
                    - :exc:`~.commands.EmojiNotFound`
                    - :exc:`~.commands.GuildStickerNotFound`
                    - :exc:`~.commands.PartialEmojiConversionFailure`
                    - :exc:`~.commands.BadBoolArgument`
                    - :exc:`~.commands.ThreadNotFound`
                    - :exc:`~.commands.FlagError`
                        - :exc:`~.commands.BadFlagArgument`
                        - :exc:`~.commands.MissingFlagArgument`
                        - :exc:`~.commands.TooManyFlags`
                        - :exc:`~.commands.MissingRequiredFlag`
                - :exc:`~.commands.BadUnionArgument`
                - :exc:`~.commands.BadLiteralArgument`
                - :exc:`~.commands.ArgumentParsingError`
                    - :exc:`~.commands.UnexpectedQuoteError`
                    - :exc:`~.commands.InvalidEndOfQuotedStringError`
                    - :exc:`~.commands.ExpectedClosingQuoteError`
            - :exc:`~.commands.CommandNotFound`
            - :exc:`~.commands.CheckFailure`
                - :exc:`~.commands.CheckAnyFailure`
                - :exc:`~.commands.PrivateMessageOnly`
                - :exc:`~.commands.NoPrivateMessage`
                - :exc:`~.commands.NotOwner`
                - :exc:`~.commands.MissingPermissions`
                - :exc:`~.commands.BotMissingPermissions`
                - :exc:`~.commands.MissingRole`
                - :exc:`~.commands.BotMissingRole`
                - :exc:`~.commands.MissingAnyRole`
                - :exc:`~.commands.BotMissingAnyRole`
                - :exc:`~.commands.NSFWChannelRequired`
            - :exc:`~.commands.DisabledCommand`
            - :exc:`~.commands.CommandInvokeError`
            - :exc:`~.commands.CommandOnCooldown`
            - :exc:`~.commands.MaxConcurrencyReached`
        - :exc:`~.commands.ExtensionError`
            - :exc:`~.commands.ExtensionAlreadyLoaded`
            - :exc:`~.commands.ExtensionNotLoaded`
            - :exc:`~.commands.NoEntryPointError`
            - :exc:`~.commands.ExtensionFailed`
            - :exc:`~.commands.ExtensionNotFound`
    - :exc:`~.ClientException`
        - :exc:`~.commands.CommandRegistrationError`
