# Arena-Hard-Auto-Toolkit-Run

## Submit toolkit run
```
eai job new -f job.yml
```

## Sample job.yml file
```image: registry.console.elementai.com/snow.core_llm/eval_framework:tgi-1.4.2

data:
    - snow.{your account name}.home:/mnt/home:rw
    - snow.core_llm.eval:/mnt/eval:rw

environmentVars:
    - EVAL_FW_WANDB_PROJECT_NAME=eval-arena-hard
    - EVAL_FW_MODEL_NAME={input your model name }
    - EVAL_FW_MODEL_URL={input your model endpoint }
    - CLAE_FW_JUDGE_MODEL_NAME={input your judge model deploy name }
    - CLAE_FW_JUDGE_MODEL_URL={input your judge model url}
    - CLAE_FW_JUDGE_MODEL_API_VERSION={input your judge model api version}
    - CLAE_FW_JUDGE_MODEL_API_KEY={input your judge model api key}

interactive: true

resources:
  mem: 256
  cpu: 1

command:
- /bin/bash
- -c
- /mnt/eval/evaluation_framework/scripts/start_evaluation_arena_hard.sh
```
## Check results
output will be synced to /mnt/eval/evaluation_framework/results/eval-arena-hard/{$EVAL_FW_MODEL_NAME}/leaderboard


