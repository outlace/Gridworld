# Gridworld
Simple implementation of text-based Gridworld game. Intended for use with reinforcement learning algorithms.

As described in this blog post: < http://outlace.com/Reinforcement-Learning-Part-3/ >



### Basic usage:

```python
import Gridworld as gw
```

Initialize game state using `initGrid` (initializes stationary grid, all items are placed deterministically), `initGridPlayer` (initializes player in random location, but keep wall, goal and pit stationary), or `initGridRand` in which all pieces are initialized to random locations on the board.


```python
state = gw.initGridRand()
gw.dispGrid(state)
```




    array([['+', '-', 'P', ' '],
           [' ', 'W', ' ', ' '],
           [' ', ' ', ' ', ' '],
           [' ', ' ', ' ', ' ']],
          dtype='<U2')



"P" represents the player, "W" is the wall (an obstacle), and "-" is the pit (a trap that gives a negative reward) and "+" is the goal which gives positive reward and wins the game.

The player makes moves with the `makeMove(state, move)` where `state` is the game state and `move` is an integer `0,1,2, or 3` which translates to 0 = up, 1 = down, 2 = left, 3 = right.


```python
state = gw.makeMove(state, 1) #Down 1 unit
state = gw.makeMove(state, 1) #Down 1 unit
state = gw.makeMove(state, 2) #Left 1 unit
state = gw.makeMove(state, 2) #Left 1 unit
state = gw.makeMove(state, 0) #Up 1 unit
state = gw.makeMove(state, 0) #Up 1 unit
```


```python
print('Reward: %s' % (gw.getReward(state),))
gw.dispGrid(state)
```

    Reward: 10





    array([[' ', '-', ' ', ' '],
           [' ', 'W', ' ', ' '],
           [' ', ' ', ' ', ' '],
           [' ', ' ', ' ', ' ']],
          dtype='<U2')



`P` player disappears when it encounters the goal or pit.


```python

```
