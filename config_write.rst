.. HuskyCrates - Last updated v1.7.2
.. highlight:: none

Configuration
===============================
.. image:: http://i.imgur.com/ZRN1RVN.png

************
Starting Out
************

Any time you get confused during this process save yourself the stress and join `our support discord`_ for realtime help on writting your config file.

Use the sidebar as your guide on where fields are in terms of brace or bracket ladders.

We suggest using an app such as Sublime Text which has a HOCON module that can aid you in properly formatting your config files.

**Very important:** Please make sure you save your config in UTF-8 ecoding the *first* time you save! It will prevent a lot of potential problems for your config.
Please note that HOCON does sort everything within ladders alphabetically.

***********
Terminology
***********

**List, Map or Dictionary**
This has to do with

****************
huskycrates.conf
****************

::
	# Message configuration.
	# If you used HuskyCrates 1.x, this is like lang{}
	# Here you set messages for the whole plugin.
	messages {
	    balanceCommand { # Messages pertaining to the balance command.
	        balanceRow="&7 - {key}&r&7: &a{amount}"
	        noBalanceEntries="&7This user has no balances."
	        noValidUser="&cNo valid user found to list the balance of."
	        otherBalanceHeader="&6{player}'s Key Balances"
	        selfBalanceHeader="&aYour Key Balances"
	        userNotExist="&c{username} has never logged into this server."
	        uuidBalanceHeader="&2Balance for {uuid}"
	    }
	    blockCommand { # Messages pertaining to the block command (/hc block)
	        itemOnlyFailure="&cThe block you supplied could not be converted to an item. Please try again with a different block."
	        noPlayersFound="&cNo valid players could be found to give a crate placement block to."
	    }
	    crate { # Messages involving a crate or crate related events.
	        rejectionCooldown="&cYou currently have {cooldown.remaining} second{cooldown.remaining.plural} out of {cooldown.total} remaining left in your cooldown."
	        rejectionNeedKey="&cYou need {key.0.amountRequired} {key.0.name}&r&c to use this crate."
	        virtualKeyConsumed="&eYou just used {amount} {key}{amount.plural}&r&e from your key balance. You have {amountRemaining} {key}&r&e{amountRemaining.plural} left."
	    }
	    keyCommand { # Messages related to the key command (/hc key)
	        crateKeyVirtual="&cThe resolved key is virtual only. Please supply a key that can be a physical item, or use the \"v\" flag."
	        crateNoLocalKey="&cThe supplied crate did not have a local key."
	        keyDeliveryFail="&c{player} failed to receive their {amount} key{amount.plural}!"
	        keyDeliverySuccess="&a{player} received {amount} key{amount.plural}."
	        massKeyDeliverySuccess="&a{playerAmount} player{playerAmount.plural} received {amount} key{amount.plural}."
	        noPlayersFound="&cNo valid players could be found to deliver keys to."
	        receivedKey="&aYou received {amount} {key}{amount.plural}&r!"
	        selfKeyDeliveryFail="&cFailed to give you keys!"
	        selfKeyDeliverySuccess="&aYou were given {amount} key{amount.plural}."
	    }
	}

	# The entry below defines if keys will be checked for uniqueness or not. Enabling this after
	# crating keys with it enabled will cause problems.
	secureKeys=true

***********
crates.conf
***********
::
	# You can define crates inside of crates.conf.
	command {
	    cooldownSeconds=0
	    effects {
	        idle {
	            particles=[
	                {
	                    animationPreset=orbit
	                    color=[
	                        0,
	                        255,
	                        0
	                    ]
	                    type="minecraft:redstone_dust"
	                },
	                {
	                    animationPreset=counterorbit
	                    color=[
	                        255,
	                        0,
	                        255
	                    ]
	                    type="minecraft:redstone_dust"
	                }
	            ]
	        }
	    }
	    free=false
	    hologram {
	        lines=[
	            "&3Command Crate"
	        ]
	    }
	    localKey {
	        id="minecraft:dirt"
	        name="&3Command Crate&r Key"
	    }
	    name="&3Command Crate"
	    slots=[
	        {
	            chance=1.0
	            displayItem {
	                count=1
	                id="minecraft:diamond"
	                lore=[
	                    "10 Minecraft Diamond"
	                ]
	                name="Diamond Box"
	            }
	            rewards=[
	                {
	                    data="give %p minecraft:diamond 10"
	                    type=servercommand
	                }
	            ]
	        },
	        {
	            chance=1.0
	            displayItem {
	                count=2
	                id="minecraft:planks"
	                lore=[
	                    Speakerbox
	                ]
	                name=BLAM
	            }
	            rewards=[
	                {
	                    data="say %p is a potato."
	                    type=servercommand
	                },
	                {
	                    type=key
	                    data="LOCALKEY_command"
	                    keyCount=5
	                }
	            ]
	        },
	        {
	            chance=1.0
	            displayItem {
	                count=3
	                id="minecraft:stone"
	                lore=[
	                    "try again BOI"
	                ]
	                name="&4be a sore loser"
	            }
	            rewards=[
	                {
	                    data="say reeee"
	                    type=servercommand
	                }
	            ]
	        },
	        {
	            chance=1.0
	            displayItem {
	                count=4
	                id="minecraft:dirt"
	                lore=[
	                    "10 Minecraft Diamond"
	                ]
	                name=trash
	            }
	            rewards=[
	                {
	                    data="say meh"
	                    type=servercommand
	                }
	            ]
	        }
	    ]
	    useLocalKey=true
	    viewOptions {
	        tickDelayMultiplier=1.025
	        ticksToSelection=100
	        ticksToSelectionVariance=3
	    }
	    viewType=roulette
	    messages {
	        rejectionNeedKey="you need a key you dummy."
	    }
	}

***********
Crate Types
***********

``type="<options_below>"``

*Spinner View* ``spinner`` - Traditional HuskyCrates view, similar to CS:GO case. Items scroll randomly until an item is picked, `spinner view is customizeable.`_

.. image:: spinner.png
    :width: 350px

*Roulette View* ``roulette`` - You have 10 seconds to make a selection, weight still affects how often items appear.

.. image:: roulette.png
    :width: 350px

*Instant View* ``instant`` - No GUI is shown and items are recieved instantly with only a rewarding message appearing.

*Simple View* ``simple`` - Basically an instant view but with a short GUI display similar to roulette view.


**********
Conclusion
**********

If you made it here you successfully built a HuskyCrates config! Now that you have your config built check out the commands page in the sidebar if you haven't already. Go test your config, if you run into any problems make sure you check your syntax to make sure you didn't leave a brace or bracket without a friend or forgot a comma between items. The server console can help you in finding these issues as well by indicating the line in the config and the issue it has with it.

.. _our support discord: http://discord.gg/FSETtcx
.. _Look here for how to use lang.: http://com.com/
.. _count: http://huskycrates.readthedocs.io/en/1.7.x/config_write.html#count
.. _click here to use a color picker: https://www.google.com/search?q=rgb+color+picker
.. _spinner view is customizeable.: http://com.com/
