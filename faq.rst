.. HuskyCrates - Last updated v1.7.2

Frequently Asked Questions
===========================

How can I use multiple commands or give multiple items for a reward?
--------------------------------------------------------------------

It's rather simple. Instead of this...

::

    rewards=[
        {
            command="money add %p 99"
            type=command
        }
    ]

Write this...

::

    rewards=[
        {
            command="money add %p 99"
            type=command
        }, # You are not required to use a certain amount of rewards. You could have 300 rewards if you wanted
        {
            command="tell %p you're cool, u know that?"
            type=command
        }, # Note, you need a comma on the closing brace before the next opening brace.
        {
            overrideItem={...} # Refer to other documentation for item format.
            type=item
        }
    ]
    
... And then you will have 3 different rewards.

 
