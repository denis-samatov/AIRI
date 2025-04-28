# DreamerV3 CartPole-v1 Experiments

A showcase of training and evaluating DreamerV3 (and PPO) on the CartPole-v1 environment using Eclectic-Sheep's SheepRL (`sheelprl`) framework.

---

## Table of Contents

- [DreamerV3 CartPole-v1 Experiments](#dreamerv3-cartpole-v1-experiments)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Dependencies](#dependencies)
  - [Usage](#usage)
    - [Clone Repository](#clone-repository)
    - [Train DreamerV3 Agent](#train-dreamerv3-agent)
    - [Train PPO Agent](#train-ppo-agent)
    - [Visualize with TensorBoard](#visualize-with-tensorboard)
  - [Directory Structure](#directory-structure)

---

## Installation

Install the required Python packages by running:

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

All required packages are listed in `requirements.txt`. Key components include:

- **Lightning Fabric** (`lightning`)
- **Hydra / OmegaConf** (`hydra-core`, `omegaconf`)
- **Gymnasium** (`gymnasium`, `gymnasium[atari]`)
- **DM Control Suite** (`dm_control`)
- **TensorBoard** (`tensorboard`)
- **MoviePy** (`moviepy`)
- Image/video helpers (`opencv-python`, `torchvision`, `python-dotenv`, `rich`)

Install them with:

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

Run DreamerV3 on CartPole-v1:

```bash
python sheeprl.py \
  exp=dreamer_v3 \
  env=gym env.id=CartPole-v1 \
  fabric.accelerator=cpu fabric.devices=1 \
  env.num_envs=1 env.sync_env=true
```

### Train PPO Agent

Run PPO on CartPole-v1:

```bash
python sheeprl.py \
  exp=ppo \
  env=gym env.id=CartPole-v1 \
  fabric.accelerator=cpu fabric.devices=1 \
  env.num_envs=1 env.sync_env=true
```

### Visualize with TensorBoard

After training, launch TensorBoard to inspect logs:

```bash
tensorboard --logdir logs/runs
```

---

## Directory Structure

```
sheeprl/                               # Root of cloned SheepRL repo
├── logs/                              # Training outputs
│   └── runs/                          # Organized by experiment and env
│       ├── dreamer_v3/                # DreamerV3 runs
│       │   └── CartPole-v1/           # CartPole-specific logs
│       │       └── 2025-04-28_18-06... # Timestamped run folders
│       │           └── version_0/     # Versioning for reproducibility
│       │               ├── checkpoints/  # .ckpt model files
│       │               ├── events.out.*   # TensorBoard event logs
│       │               └── hparams.yaml   # Hyperparameter snapshot
│       └── ppo/                       # PPO runs (same structure)
├── sheeprl.py                         # Main CLI entrypoint
└── requirements.txt                   # Python dependencies
```

