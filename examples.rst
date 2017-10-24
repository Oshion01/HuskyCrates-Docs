.. HuskyCrates - Last updated v1.7.2
.. highlight:: none

Examples
===============================


^^^^^^^^^^^^^^^^^^^
Fake State Of Sponge XIV Config
^^^^^^^^^^^^^^^^^^^

::

    crates {
      sosbasic {
          items=[
              {
                  count=2
                  damage=3
                  formatversion=1
                  huskydata {
                      reward {
                          overrideRewardName=BLAM
                          type=item
                      }
                      weight=1
                  }
                  id="minecraft:planks"
                  lore=[
                      Speakerbox
                  ]
                  name=BLAM
              },
              {
                  count=2
                  formatversion=1
                  huskydata {
                      reward {
                          command="smite %p"
                          type=command
                      }
                      weight=3
                  }
                  id="minecraft:ender_pearl"
                  lore=[
                      "&7Legend has it, just looking at this",
                      "&7pearl causes localized lightning."
                  ]
                  name="&bLightning Pearl"
              }
          ]
          name="&eSoS &6XIV &7Basic"
          options {
              # optional
              crateBlockID="minecraft:sponge"
              keyID="minecraft:iron_nugget"
              particle1 {
                  color=[
                      150,
                      150,
                      0
                  ]
              }
              particle2 {
                  color=[
                      100,
                      100,
                      0
                  ]
              }
          }
          spinnerOptions {
              # optional
              # default (1.05)
              dampening=1.025
              # default is zero for min and max
              # maxClickModifier=3
              # default 45
              maxClicks=50
          }
          type=Roulette
      }
      sosbattle {
          items=[
              {
                  count=1
                  formatversion=1
                  huskydata {
                      reward {
                          type=item
                      }
                      weight=1
                  }
                  id="minecraft:stick"
                  lore=[
                      "&bbrr brr brr brr"
                  ]
                  name="&3Chill Stick"
              }
          ]
          lang {
              prefix="&c&lARENA&r&e>> "
              rewardMessage="Have %a &a%R&r!"
          }
          name="&aSoS &6XIV &l&cArena"
          options {
              # optional
              crateBlockID="minecraft:ender_chest"
              freeCrate=true
              freeCrateDelay=5
              particle1 {
                  color=[
                      255,
                      72,
                      0
                  ]
              }
              particle2 {
                  color=[
                      190,
                      190,
                      0
                  ]
              }
          }
          spinnerOptions {
              # optional
              # default (1.05)
              dampening=1.025
              # default is zero for min and max
              # maxClickModifier=3
              # default 45
              maxClicks=50
          }
          type=instant
      }
      soscool {
          items=[
              {
                  count=1
                  enchants {
                      knockback=255
                      satan=55
                  }
                  formatversion=1
                  huskydata {
                      reward {
                          type=item
                      }
                      weight=1
                  }
                  id="minecraft:stick"
                  name="&4Bitchin Stick"
              }
          ]
          name="&eSoS &6XIV &aCool"
          options {
              # optional
              crateBlockID="minecraft:sponge"
              keyID="minecraft:gold_nugget"
              particle1 {
                  color=[
                      255,
                      255,
                      0
                  ]
              }
              particle2 {
                  color=[
                      150,
                      150,
                      0
                  ]
              }
          }
          spinnerOptions {
              # optional
              # default (1.05)
              dampening=1.025
              # default is zero for min and max
              # maxClickModifier=3
              # default 45
              maxClicks=50
          }
          type=Spinner
      }
    }
    lang {
      # noKeyMessage="You need a key for this %c..."
      prefix="&6SoS XIV&e>> "
      # rewardAnnounceMessage="%p won %a %r from a neato %c!"
      rewardMessage="You got %a &a%R&r!"
    }

