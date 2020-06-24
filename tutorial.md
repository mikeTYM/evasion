# Evasion

## Introduction @unplugged

Build a simple game using the 25 LED "screen". Move your "ship", using the A and B buttons, to avoid the alien "ship". Compete for the highest score!


## Make a sprite variable

Create a new variable called `ship`. Drag a ``||variables:set sprite to||`` into the ``||basic:on start||`` on the workspace. 

```blocks
let ship = 0
```
## Create a sprite

Pull out a ``||game:create sprite||`` block and put it in ``||variables:set sprite to||`` replacing the `0`. A sprite is a single pixel that can move on the screen. It has an ``x`` and ``y`` position along with a direction of motion.

```blocks
let ship = game.createSprite(2, 2)
```

## Create another sprite variables

Create another new variable called `alien_ship`. Drag a ``||variables:set sprite to||`` into the ``||basic:on start||`` on the workspace. 

```blocks
let alien_ship = 0
```

## Create another sprite

Pull out another ``||game:create sprite||`` block and put it in ``||variables:set sprite to||`` replacing the `0`. A sprite is a single pixel that can move on the screen. It has an ``x`` and ``y`` position along with a direction of motion.
Now, let's add ``||math:randint||`` block to the X and Y positions. We want a random number between 0 and 4.
```blocks
let alien_ship = game.createSprite(randint(0,4), randint(0,4))
```

## Alien Ship Movement

Place a ``||loop:while||`` block inside the ``||basic: on start||`` block. 
Set the x and y positions of the `alien_ship` variable to 
a random number between 0 and 4. Add a 1 second pause.
```blocks
while (true) {
let alien_ship: game.LedSprite = null
alien_ship.set(LedSpriteProperty.Y, randint(0,4))
alien_ship.set(LedSpriteProperty.X, randint(0,4))
basic.pause(1000)
}
```

## Collision Detection
Place a ``||logic: if ||`` block inside the ``||basic:forever||`` block. Place a
``||game: is touching ||`` block in the ``||logic: if||`` block to check to see if your
ship collides with the alien ship. If it does - Game Over!

```blocks
let ship: game.LedSprite = null
basic.forever(function () {
    if (ship.isTouching(alien_ship)) {
        game.gameOver()
    }
})
```

## Move to the left

When **A** is pressed, we move your ship to the left. We also add 1 to our score.

Use a ``||input:on button pressed||`` block to handle the **A** button.

```blocks
let ship: game.LedSprite = null
input.onButtonPressed(Button.A, function () {
    ship.move(-1)
    game.setScore(game.score() + 1)
}
```

## Move to the right

When **B** is pressed, we move your ship to the right. We also add 1 to our score.

Use a ``||input:on button pressed||`` block to handle the **B** button.

```blocks
let ship: game.LedSprite = null
input.onButtonPressed(Button.B, function () {
    ship.move(1)
    game.setScore(game.score() + 1)
}
```
## Turn right

When **A+B** is pressed, we move your ship to the right. We also add 1 to our score.

Use a ``||input:on button pressed||`` block to handle the **A+B** button.

```blocks
let ship: game.LedSprite = null
input.onButtonPressed(Button.AB, function () {
    ship.turn(Direction.Right, 90)
    game.setScore(game.score() + 1)
}
```

## Test and download

Your game is ready! If you have a @boardname@, press ``|Download|`` to try it out on the device.

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
