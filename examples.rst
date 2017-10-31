.. HuskyCrates - Last updated v1.7.2
.. highlight:: none

Examples
===============================

**Please note that these examples need to be updated with the new reward format which allows for multiple rewards.**

^^^^^^^^^^^^^^^^^^^
Simple crates
^^^^^^^^^^^^^^^^^^^

::

    crates {
        command {
            items=[
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            command="give %p minecraft:diamond 10"
                            overrideRewardName="Diamond Box"
                            type=command
                        }
                        weight=1
                    }
                    id="minecraft:stone"
                    lore=[
                        "10 Minecraft Diamond"
                    ]
                    name="Diamond Box"
                    type=Spinner
                },
                {
                    count=2
                    damage=3
                    formatversion=1
                    huskydata {
                        reward {
                            command="say %p is a potato."
                            overrideRewardName=BLAM
                            type=command
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
                    count=3
                    formatversion=1
                    huskydata {
                        reward {
                            command="crate key command %p"
                            overrideRewardName="be a sore loser"
                            type=command
                        }
                        weight=1
                    }
                    id="minecraft:stone"
                    lore=[
                        "try again BOI"
                    ]
                    name="&4be a sore loser"
                },
                {
                    count=4
                    formatversion=1
                    huskydata {
                        reward {
                            command="say meh"
                            overrideRewardName=trash
                            type=command
                        }
                        weight=1
                    }
                    id="minecraft:dirt"
                    lore=[
                        "10 Minecraft Diamond"
                    ]
                    name=trash
                }
            ]
            name="&3Command Crate"
            options {
                keyID="minecraft:dirt"
                particle1 {
                    color=[
                        #                                              red 
                        97,
                        #                                              green 
                        186,
                        #                                              blue
                        39
                    ]
                }
                particle2 {
                    color=[
                        255,
                        0,
                        255
                    ]
                }
            }
            spinnerOptions {
                dampening=1.025
                maxClickModifier=3
                maxClicks=100
                minClickModifier=-3
            }
            type=Spinner
        }
        fancy {
            items=[
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=5
                    }
                    id="minecraft:diamond"
                    name="minecraft:diamond"
                },
                {
                    count=15
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=20
                    }
                    id="minecraft:dirt"
                    name="minecraft:dirt"
                },
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=1
                    }
                    id="minecraft:cobblestone"
                    lore=[
                        "He once was a spooky stones."
                    ]
                    name="&3Stoned the Stones"
                },
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=1
                    }
                    id="minecraft:planks"
                    lore=[
                        ":)"
                    ]
                    name="&6Pre-cut wood"
                },
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=1
                    }
                    id="minecraft:diamond_sword"
                    lore=[
                        "idk someone gave it to me."
                    ]
                    name="&cFancy sword"
                }
            ]
            name="&bFancy Cool Crate"
            options {
                particle1 {
                    color=[
                        #                                              red 
                        0,
                        #                                              green 
                        255,
                        #                                              blue
                        255
                    ]
                }
                particle2 {
                    color=[
                        255,
                        255,
                        0
                    ]
                }
            }
            type=Spinner
        }
        mining {
            items=[
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=5
                    }
                    id="minecraft:diamond"
                    name="minecraft:diamond"
                },
                {
                    count=15
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=20
                    }
                    id="minecraft:dirt"
                    name="minecraft:dirt"
                },
                {
                    count=1
                    enchants {
                        sharpness=255
                    }
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=1000
                    }
                    id="minecraft:cobblestone"
                    lore=[
                        "He once was a spooky stones."
                    ]
                    name="&3Stoned the Stones"
                },
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=1
                    }
                    id="minecraft:planks"
                    lore=[
                        ":)"
                    ]
                    name="&6Pre-cut wood"
                },
                {
                    count=1
                    formatversion=1
                    huskydata {
                        reward {
                            type=item
                        }
                        weight=1
                    }
                    id="minecraft:diamond_sword"
                    lore=[
                        "idk someone gave it to me."
                    ]
                    name="&cFancy sword"
                }
            ]
            name="§8Mining Crate"
            options {
                particle1 {
                    color=[
                        #                                              red 
                        175,
                        #                                              green 
                        175,
                        #                                              blue
                        175
                    ]
                }
                particle2 {
                    color=[
                        255,
                        0,
                        0
                    ]
                }
            }
            type=Spinner
        }
    }


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

