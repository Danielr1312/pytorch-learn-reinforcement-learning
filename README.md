## Reinforcement Learning (PyTorch) :robot: + :cake: = :heart:

This repo will contain PyTorch implementation of various fundamental RL algorithms. <br/>
It's aimed at making it **easy** to start playing and learning about RL. <br/>

The problem I came across investigating other DQN projects is that they either:
* Don't have any evidence that they've actually achieved the published results 
* Don't have a "smart" replay buffer (i.e. they allocate (1M, 4, 84, 84) bytes instead of (1M, 84, 84) ~ 7 GB)
* Lack of visualizations and debugging utils

This repo will aim to solve these problems.

## Table of Contents
* [DQN](#dqn)
* [Setup](#setup)
* [Usage](#usage)
* [Hardware requirements](#hardware-requirements)
* [Learning material](#learning-material)

## DQN

This was the project that started the revolution in the RL world - deep Q-network (:link: [Mnih et al.](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf)),
aka "Human-level control through deep RL".

DQN model learned to play **29 Atari games** (out of 49 they it tested on) on a **super-human**/comparable-to-humans level.

<p align="center">
<img src="data/readme_pics/dqn.jpg" width="800"/>
</p>

---

Since it takes lots of compute and time to train all of the 49 models I'll consider this DQN project completed once
I succeed in achieving the published results on:
* Breakout
* Pong

Having said that the experiments are still in progress, so feel free to **contribute**!
* For some reason the models aren't learning very well so if you find a bug open up a PR! :heart:
* If you decide to train the DQN using this repo on some other Atari game I'll gladly check-in your model!

### Current results - Breakout

<p align="center">
<img src="data/gifs/BreakoutNoFrameskip-v4_1.gif" />
</p>

As you can see the model did learn something although it's far from being really good.

### Current results - Pong

todo

## Setup

Let's get this thing running! Follow the next steps:

1. `git clone https://github.com/gordicaleksa/pytorch-learn-reinforcement-learning`
2. Open Anaconda console and navigate into project directory `cd path_to_repo`
3. Run `conda env create` from project directory (this will create a brand new conda environment).
4. Run `activate pytorch-rl-env` (for running scripts from your console or setup the interpreter in your IDE)

If you're on Windows you'll additionally need to install this:
`pip install https://github.com/Kojoley/atari-py/releases atary_py` to install gym's Atari dependencies.

Otherwise this should do it `pip install 'gym[atari]'`, if not check out [this](https://stackoverflow.com/questions/49947555/openai-gym-trouble-installing-atari-dependency-mac-os-x) and [this](https://github.com/openai/gym/issues/1170).

That's it! It should work out-of-the-box executing environment.yml file which deals with dependencies. <br/>

-----

PyTorch pip package will come bundled with some version of CUDA/cuDNN with it,
but it is highly recommended that you install a system-wide CUDA beforehand, mostly because of the GPU drivers. 
I also recommend using Miniconda installer as a way to get conda on your system.
Follow through points 1 and 2 of [this setup](https://github.com/Petlja/PSIML/blob/master/docs/MachineSetup.md)
and use the most up-to-date versions of Miniconda and CUDA/cuDNN for your system.

## Usage

#### Option 1: Jupyter Notebook

Coming soon.

#### Option 2: Use your IDE of choice

You just need to link the Python environment you created in the [setup](#setup) section.

## Hardware requirements

You'll need some decent hardware to train the DQN in reasonable time so that you can iterate:
1) **16+ GB of RAM** (Replay Buffer takes around ~7 GBs of RAM).
2) The faster your GPU is - the better (well duh). Having said that VRAM is not the bottleneck you'll need **~ 2 GB VRAM**.

With 16 GB RAM and RTX 2080 it takes ~5 days to train DQN on my machine - I'm **experiencing some slowdowns** which I
haven't debugged yet. Here is the FPS (frames-per-second) metric I'm logging:

<p align="center">
<img src="data/metrics/fps_metric.PNG"/>
</p>

The shorter, green one is the current experiment I'm running, the red one took over 5 days to train.

## Learning material

Here are some videos I made on RL which may help you to better understand how DQN and other RL algorithms work:

<p align="left">
<a href="https://www.youtube.com/watch?v=H1NRNGiS8YU" target="_blank"><img src="https://img.youtube.com/vi/H1NRNGiS8YU/0.jpg" 
alt="DQN paper explained" width="480" height="360" border="10" /></a>
</p>

And some other ones:
* [DeepMind: AlphaGo](https://www.youtube.com/watch?v=Z1BELqFQZVM)
* [DeepMind: AlphaGo Zero and AlphaZero](https://www.youtube.com/watch?v=0slFo1rV0EM)
* [OpenAI: Solving Rubik's Cube with a Robot Hand](https://www.youtube.com/watch?v=eTa-k1pgvnU)
* [DeepMind: MuZero](https://www.youtube.com/watch?v=mH7f7N7s79s)

And in this one I tried to film through the process while the project was not nearly as polished as it is now:
* [DQN project update](https://www.youtube.com/watch?v=DrOp_MQGn9o&ab_channel=TheAIEpiphany)

I'll soon create a blog on how to get started with RL - so stay tuned for that!

## Acknowledgements

I found these resources useful while developing this project, sorted (approximately) by usefulness:

* [Stable Baselines 3 DQN](https://github.com/DLR-RM/stable-baselines3/blob/master/stable_baselines3/dqn/dqn.py)
* [PyTorch reimplementation of Berkley's DQN](https://github.com/transedward/pytorch-dqn) and [Berkley's DQN](https://github.com/berkeleydeeprlcourse/homework/tree/master/hw3)
* [pytorch-dqn](https://github.com/jacobaustin123/pytorch-dqn/blob/master/dqn.py)
* [RL adventures DQN](https://github.com/higgsfield/RL-Adventure/blob/master/1.dqn.ipynb) and [minimal DQN](https://github.com/econti/minimal_dqn/blob/master/main.py)
* [Pytorch tutorial](https://pytorch.org/tutorials/intermediate/reinforcement_q_learning.html)

## Citation

If you find this code useful, please cite the following:

```
@misc{Gordić2021PyTorchLearnReinforcementLearning,
  author = {Gordić, Aleksa},
  title = {pytorch-learn-reinforcement-learning},
  year = {2021},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/gordicaleksa/pytorch-learn-reinforcement-learning}},
}
```

## Licence

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/gordicaleksa/pytorch-learn-reinforcement-learning/blob/master/LICENCE)