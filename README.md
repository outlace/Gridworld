# Gridworld
Simple implementation of text-based Gridworld game. Intended for use with reinforcement learning algorithms.

As described in this blog post: < http://outlace.com/rlpart3.html >



### Basic usage:

```python
from Gridworld import *
```

Initialize game state using `initGrid` (initializes stationary grid, all items are placed deterministically), `initGridPlayer` (initializes player in random location, but keep wall, goal and pit stationary), or `initGridRand` in which all pieces are initialized to random locations on the board.


```python
game = Gridworld(size=4, mode='static')
game.dispGrid()
```




    array([['+', '-', 'P', ' '],
           [' ', 'W', ' ', ' '],
           [' ', ' ', ' ', ' '],
           [' ', ' ', ' ', ' ']],
          dtype='<U2')



"P" represents the player, "W" is the wall (an obstacle), and "-" is the pit (a trap that gives a negative reward) and "+" is the goal which gives positive reward and wins the game.

The player makes moves with the `game.makeMove(move)` where  `move` is a character `u,d,l, or r` for up,down, left or right.


```python
game.makeMove('d') # (0,3) + (-1,3)
print("Reward: %s" % (game.getReward()))
game.dispGrid()
```

```
Reward: -1

array([[' ', ' ', ' ', ' ', '+'],
       [' ', ' ', ' ', ' ', ' '],
       [' ', ' ', 'P', ' ', ' '],
       [' ', ' ', '-', ' ', ' '],
       [' ', ' ', ' ', 'W', ' ']], dtype='<U2')
```

Use the `render_np()` method to produce a numpy tensor to supply to a machine learning algorithm.
```python
game.board.render_np()
```

```
array([[[0, 0, 0, 1, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0]],

       [[1, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0]],

       [[0, 1, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0]],

       [[0, 0, 0, 0, 0],
        [0, 1, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0]]], dtype=uint8)

```
