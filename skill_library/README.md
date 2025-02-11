# Learned Skill Libraries

## Default Libraries

* [skill_library/trial1](trial1)
* [skill_library/trial2](trial2)
* [skill_library/trial3](trial3)

## How to Contribute

After you run the learning process, you will see a checkpoint directory like:
```
.
├── action
│   └── chest_memory.json
├── curriculum
│   ├── completed_tasks.json
│   ├── failed_tasks.json
│   ├── qa_cache.json
│   └── vectordb
├── events
└── skill
    ├── code
    │   ├── catchThreeFishWithCheck.js
    │   ├── collectBamboo.js
    │   ├── ...
    ├── description
    │   ├── catchThreeFishWithCheck.txt
    │   ├── collectBamboo.txt
    │   └── ...
    ├── skills.json
    └── vectordb
```

Only `YOUR_CKPT_DIR/skill` is a learned skill library, which you can share with others. Create a pull request to add your skill library to this repository.