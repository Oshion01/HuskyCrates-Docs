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
		
		# Messages pertaining to the balance command.
	    balanceCommand { 
	        balanceRow="&7 - {key}&r&7: &a{amount}"
	        noBalanceEntries="&7This user has no balances."
	        noValidUser="&cNo valid user found to list the balance of."
	        otherBalanceHeader="&6{player}'s Key Balances"
	        selfBalanceHeader="&aYour Key Balances"
	        userNotExist="&c{username} has never logged into this server."
	        uuidBalanceHeader="&2Balance for {uuid}"
	    }

	    # Messages pertaining to the block command (/hc block)
	    blockCommand { 
	        itemOnlyFailure="&cThe block you supplied could not be converted to an item. Please try again with a different block."
	        noPlayersFound="&cNo valid players could be found to give a crate placement block to."
	    }

	    # Messages involving a crate or crate related events.
	    crate { 
	        rejectionCooldown="&cYou currently have {cooldown.remaining} second{cooldown.remaining.plural} out of {cooldown.total} remaining left in your cooldown."
	        rejectionNeedKey="&cYou need {key.0.amountRequired} {key.0.name}&r&c to use this crate."
	        virtualKeyConsumed="&eYou just used {amount} {key}{amount.plural}&r&e from your key balance. You have {amountRemaining} {key}&r&e{amountRemaining.plural} left."
	    }

	    # Messages related to the key command (/hc key)
	    keyCommand { 
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
		# Defines how long a player has to wait between free uses or key uses.
		# Unlike v1.x, v2.x allows you to limit key use rates as well.
	    cooldownSeconds=0

	    # Effects is a new system allowing for completely customizable
	    # crate effects. You can also trigger them via rewards.
	    # The effect format will be gone over in more detail later.
	    # 
	    # No effects will play by default for idle, but reject has a default smoke
	    # effect. Overriding both with no-particle effects will effectively
	    # disable them. Also, setting "disabled=true" will disable an effect.
	    effects {

	    	# "idle" is the effect that plays while a crate is not in use.
	    	# This example follows a HuskyCrates v1.x-like pattern.
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

	        # "reject" is the particle effect that plays when a player is rejected from a crate.
	        # This example forms 16 red particle circles from the ground up.
	        reject {
	            duration=16
	            loop=false
	            resetOnTimeout=true
	            particles=[
	                {
	                    type="minecraft:redstone_dust"
	                    amount=10

	                    # Custom animation code. Neat, right? Read on for more info.
	                    animationCode="var spin = time/3; x=Math.sin(spin + num)*0.7; y=(time/8) - 0.5; z=Math.cos(spin + num)*0.7;"
	                }
	            ]
	        }
	    }

	    # Basically means that this crate has no need for keys if true.
	    # This example requires a key.
	    # Same as "freeCrate" in v1.x
	    free=false

	    # Custom multi-line hologram settings.
	    # Will not have a hologram if not present.
	    hologram {
	    	# Color-code formatted lines.
	        lines=[
	            "&3Command Crate",
	            "&cWoah!!"
	        ]

	        # How far from default holograms are placed on the crate.
	        yOffset=0.0

	        # Same as previous, but just if the crate is an entity crate.
	        entityYOffset=0.0
	    }

	    # Defining a key for the crate, or a local key.
	    # This is due to the ability to create custom keys now in keys.conf.
	    # Don't worry about NBT or anything, just follow the item format.
	    localKey {
	        id="minecraft:dirt"
	        name="&3Command Crate&r Key"
	    }

	    # Name, displayed in inventory gui.
	    name="&3Command Crate"

	    # Equiv to "items" from v1.x, except with a different layout.
	    slots=[
	        {
	        	# Same as "weight"
	        	# Chance is basically the probability of getting a specific slot
	        	# over the sum of all other slots. (slot chance / sum of slot chances)
	            chance=1.0

	            # Display item, following item format.
	            displayItem {
	                count=1
	                id="minecraft:diamond"
	                lore=[
	                    "10 Minecraft Diamond"
	                ]
	                name="Diamond Box"
	            }

	            # Pick a reward from this slot at random!
	            pickRandom=true

	            # If we pick a group of rewards, should each reward be unique in our pick?
	            pickUnique=true

	            # The amount of rewards to pick. Should be less than total amount of rewards.
	            pickSize=1
	            rewards=[
	                {
	                	# Runs /give ... as the server.
	            		# Rewards are relatively simple, but will be gone over in detail in another
	            		# section.
	                    data="give %p minecraft:diamond 10"
	                    type=servercommand
	                },
	                [ # Reward Group
	                	{
	                		data="You're an idiot",
	                		type=usermessage
	                	},
	                	{
	                		data="%p is an idiot"
	                		type=servermessage
	                	}
	                ]
	            ]
	        },
	        {
	        	# Example for purposes of explaining how multiple slots
	        	# should be defined.
	            ...
	        },
	        ...
	    ]

	    # If the crate should use its own key.
	    useLocalKey=true

	    # Accepted keys (in List form.)
	    acceptedKeys=[
	    	"testKey",
	    	"fakeKey"
	    ]

	    # Accepted keys (in Map form.)
	    acceptedKeys{
	    	# 1 testKey will be sufficent to use the crate.
	    	testKey=1

	    	# 5 fakeKeys will be sufficent to use the crate as well.
	    	fakeKey=5
	    }


	    viewOptions {

	    	# Border item, defaults to dark gray stained glass pane.
	    	borderItem{
	    		# Follows standard item format.
	    		...
	    	}
	    	
	    	######################
	    	## SPINNER SPECIFIC ##
	    	######################

	    	# Selector item, defaults to a redstone torch.
	    	selectorItem{
	    		# Follows standard item format.
	    		...
	    	}

	    	# How much the delay should be multiplied by each time the spinner clicks.
	        tickDelayMultiplier=1.025

	        # How many clicks should the spinner go through before stopping.
	        ticksToSelection=100

	        # How many clicks should we offset ticksToSelection by in any direction?
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
