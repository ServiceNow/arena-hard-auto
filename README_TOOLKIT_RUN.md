# Arena-Hard-Auto-Toolkit-Run

## Submit toolkit run
```
eai job new -f job.yml
```

## Sample job.yml file to run show_result.py
```
image: registry.console.elementai.com/snow.core_llm/eval_framework:tgi-1.4.2

data:
    - snow.wzhang.home:/mnt/home:rw
    - snow.core_llm.eval:/mnt/eval:rw

environmentVars:
    - ARENA_HARD_SCRIPT_NAME=show_result.py

interactive: true

resources:
  mem: 256
  cpu: 4

command:
- /bin/bash
- -c
- /mnt/eval/evaluation_framework/scripts/start_evaluation_arena_hard.sh
```

## Sample job.yml file to run gen_answer.py
```
image: registry.console.elementai.com/snow.core_llm/eval_framework:tgi-1.4.2

data:
    - snow.wzhang.home:/mnt/home:rw
    - snow.core_llm.eval:/mnt/eval:rw

environmentVars:
    - ARENA_HARD_SCRIPT_NAME=gen_answer.py
    - ARENA_HARD_GEN_ANSWER_ARGS={"model_list":["mixtral_instruct_tgi_endpoint_2"]}
    - ARENA_HARD_API_CONFIG_ARGS={"mixtral_instruct_tgi_endpoint_2":{"model_name":"mixtral_instruct_tgi_endpoint_2","endpoints":[{"mapi_base":"https://a5eb8993-9f05-40cd-b2e9-9c0b205ebd5c-8080.job.console.elementai.com/generate","api_key":"8o30OElfDYV_D6YbbznT0A:GDC2BsXIfSdfjv9iWka3V4MkazpvHfe0cCwXohzbP0Q"}],"api_type":"toolkit_tgi","parallel":50}}

interactive: true

resources:
  mem: 256
  cpu: 4

command:
- /bin/bash
- -c
- /mnt/eval/evaluation_framework/scripts/start_evaluation_arena_hard.sh
```
## Sample job.yml file to run gen_answer.py


