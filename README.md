# AI Minecraft

<img src="attached_assets/mindcraft.jpg" alt="Minecraft Banner" width="100%" style="margin-bottom: 20px"/>

[![Twitter Follow](https://img.shields.io/twitter/follow/AiMindCraft?style=social)](https://x.com/AiMindCraft)

## Introduction

We introduce Voyager, the first LLM-powered embodied lifelong learning agent in Minecraft that continuously explores the world, acquires diverse skills, and makes novel discoveries without human intervention. Voyager consists of three key components: 1) an automatic curriculum that maximizes exploration, 2) an ever-growing skill library of executable code for storing and retrieving complex behaviors, and 3) a new iterative prompting mechanism that incorporates environment feedback, execution errors, and self-verification for program improvement. 

Voyager interacts with GPT-4 via blackbox queries, which bypasses the need for model parameter fine-tuning. The skills developed by Voyager are temporally extended, interpretable, and compositional, which compounds the agent's abilities rapidly and alleviates catastrophic forgetting. Empirically, Voyager shows strong in-context lifelong learning capability and exhibits exceptional proficiency in playing Minecraft. It obtains 3.3× more unique items, travels 2.3× longer distances, and unlocks key tech tree milestones up to 15.3× faster than prior SOTA. Voyager is able to utilize the learned skill library in a new Minecraft world to solve novel tasks from scratch, while other techniques struggle to generalize.

## Upcoming Features

### Tokenomics
We are developing our own token ecosystem for AI Minecraft. The tokenomics will include:
- Native utility token for in-game transactions
- Reward mechanisms for skill development and sharing
- Governance system for community-driven development
- Staking and liquidity provision mechanisms

Stay tuned for more details about our token launch and economic model!

## Features

- Continuous exploration of the Minecraft world
- Extensible skill library
- Automatic learning and behavior improvement
- Ability to decompose and execute complex tasks

## Prerequisites

- Python ≥ 3.9
- Node.js ≥ 16.13.0
- An OpenAI API key (GPT-4)
- Minecraft with Fabric

## Installation

### 1. Python Installation

```bash
git clone [YOUR_REPO_URL]
cd [REPO_NAME]
pip install -e .
```

### 2. Node.js Installation

```bash
cd voyager/env/mineflayer
npm install -g npx
npm install
cd mineflayer-collectblock
npx tsc
cd ..
npm install
```

### 3. Minecraft Configuration

1. Install Minecraft
2. Install the required Fabric mods (see `installation/fabric_mods_install.md`)

## Usage

```python
from voyager import Agent

# Connection configuration
azure_login = {
    "client_id": "YOUR_CLIENT_ID",
    "redirect_url": "https://127.0.0.1/auth-response",
    "secret_value": "[OPTIONAL] YOUR_SECRET_VALUE",
    "version": "fabric-loader-0.14.18-1.19"
}
openai_api_key = "YOUR_API_KEY"

# Initialization
agent = Agent(
    azure_login=azure_login,
    openai_api_key=openai_api_key,
)

# Start learning
agent.learn()
```

### Minecraft World Configuration

1. Select "Singleplayer" and create a new world
2. Game Mode: "Creative", Difficulty: "Peaceful"
3. Press Esc and "Open to LAN"
4. Enable commands and start LAN world

### Resume from Checkpoint

```python
agent = Agent(
    azure_login=azure_login,
    openai_api_key=openai_api_key,
    ckpt_dir="CHECKPOINT_PATH",
    resume=True,
)
```

### Execute Specific Tasks

```python
# Load a skill library
agent = Agent(
    azure_login=azure_login,
    openai_api_key=openai_api_key,
    skill_library_dir="./skill_library/trial1",
    ckpt_dir="NEW_PATH",
    resume=False,
)

# Task decomposition and execution
task = "Craft a diamond pickaxe"
sub_goals = agent.decompose_task(task=task)
agent.inference(sub_goals=sub_goals)
```

## FAQ

For any questions, please check the FAQ.md file.

## License

This project is under MIT License.

## Social Media

Follow us on:
- Twitter: [@AiMindCraft](https://x.com/AiMindCraft)
- Telegram: [AiMindCraft Community](https://t.me/AiMindCraft)