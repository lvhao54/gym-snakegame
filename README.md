# gym-snakegame
A gymnasium-based RL environment for learning the snake game.

![snakegame5x5](https://user-images.githubusercontent.com/54899900/225275703-646f8f42-62dd-4b0d-b527-aaf93ba6e1f7.gif)

You can make a game with a grid size larger than 5x5.

| Action Space | Observation Space |
|--------------|-------------------|
|  Discrete(4) | (`size`, `size`)  |

# Installation
```bash
git clone https://github.com/helpingstar/gym-snakegame.git
cd gym-snakegame
pip install -r requirements.txt
pip install -e .
```

## Colab

```bash
!git clone https://github.com/helpingstar/gym-snakegame.git
%cd gym-snakegame
!pip install -r requirements.txt
!pip install -e .
```

# Usage
```python
import gym_snakegame
import gymnasium as gym

env = gym.make('gym_snakegame/SnakeGame-v0', size=15, n_target=1, render_mode='rgb_array')
# env = gym.wrappers.RecordVideo(env, video_folder='./video_folder', episode_trigger=lambda x: x % 200 == 0)

observation, info = env.reset()
for i in range(100000):
    action = env.action_space.sample()
    obs, reward, terminated, _, info = env.step(action)
    if terminated:
        env.reset()
env.close()
```
## parameter
* `size` : The size of a square board. The board has the shape `(size, size)`.
* `n_target` : The number of targets placed on a board.

# Observation

* `0` : snake
* `1` : blank
* `3` : head
* `5` : target

# Action

* `0` : down
* `1` : right
* `2` : up
* `3` : left
