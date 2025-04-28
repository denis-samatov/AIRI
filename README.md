# DreamerV3 CartPole-v1 Experiments

A showcase of training and evaluating DreamerV3 (and PPO) on the CartPole-v1 environment using Eclectic-Sheep's SheepRL (`sheelprl`) framework.

---

## Table of Contents

- [Installation](#installation)
- [Dependencies](#dependencies)
- [Usage](#usage)
  - [Clone Repository](#clone-repository)
  - [Train DreamerV3 Agent](#train-dreamerv3-agent)
  - [Train PPO Agent](#train-ppo-agent)
  - [Visualize with TensorBoard](#visualize-with-tensorboard)
- [Directory Structure](#directory-structure)
- [Results](#results)

---

## Installation

Install all required Python packages by running:

```bash
pip install -r requirements.txt
```

> If you are in a Jupyter or Colab environment, prepend `%` to each line:
>
> ```bash
> %pip install -r requirements.txt
> ```

---

## Dependencies

Key components are listed in `requirements.txt`:

- `lightning`, `omegaconf`, `hydra-core`, `rich`: core framework and config
- `gymnasium`, `gymnasium[atari]`, `dm_control`: environments
- `torchvision`, `moviepy`, `opencv-python`: image/video utilities
- `python-dotenv`, `tensorboard`: logging and environment

Install all with:

```bash
pip install -r requirements.txt
```

---

## Usage

### Clone Repository

```bash
git clone https://github.com/Eclectic-Sheep/sheeprl.git
cd sheeprl
```

### Train DreamerV3 Agent

Quick 10k-step demo:

```bash
python sheeprl.py \
  exp=dreamer_v3 \
  env=gym env.id=CartPole-v1 \
  fabric.accelerator=cpu fabric.devices=1 \
  env.num_envs=1 env.sync_env=true
```

### Train PPO Agent

Quick 10k-step demo:

```bash
python sheeprl.py \
  exp=ppo \
  env=gym env.id=CartPole-v1 \
  fabric.accelerator=cpu fabric.devices=1 \
  env.num_envs=1 env.sync_env=true
```

### Visualize with TensorBoard

```bash
tensorboard --logdir logs/runs
```

---

## Directory Structure

```
sheeprl/                             # Root of cloned SheepRL repo
├── logs/                            # Training outputs
│   └── runs/                        # Organized by experiment and env
│       ├── dreamer_v3/              # DreamerV3 runs
│       │   └── CartPole-v1/         # CartPole-v1 logs
│       │       └── <timestamp>/      # Timestamped run folders
│       │           ├── version_0/   # Versioning
│       │           │   ├── checkpoints/   # Saved .ckpt files
│       │           │   ├── events.out.*    # TensorBoard logs
│       │           │   └── hparams.yaml    # Hyperparam snapshot
│       └── ppo/                     # PPO runs (similar structure)
├── sheeprl.py                       # CLI entrypoint
└── requirements.txt                 # Python dependencies
```

---

## Results

All recorded videos of the trained agents are stored in the `results/` directory at the repo root:

```
results/
├── dreamer_v3/                      # DreamerV3 videos
│   └── CartPole-v1/                 # DreamerV3 CartPole-v1 runs
│       └── video.mp4                # Example rollout video
└── ppo/                             # PPO videos
    └── CartPole-v1/                 # PPO CartPole-v1 runs
        └── video.mp4                # Example rollout video
```

You can play these `.mp4` files to review agent behaviors.

