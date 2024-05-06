# WorldQA Evaluation

The evluation of WorldQA is based on the lmms-eval.

## Install
1. Install `lmms-eval` as follows
```
git clone https://github.com/EvolvingLMMs-Lab/lmms-eval
cd lmms-eval
git checkout kc/worldqa
pip install -e .
```

2. (Optional) Following the instructions in the `model` folder for [`video_llava`](https://github.com/EvolvingLMMs-Lab/lmms-eval/blob/kc/worldqa/lmms_eval/models/video_llava.py) and [`llama_vid`](https://github.com/EvolvingLMMs-Lab/lmms-eval/blob/kc/worldqa/lmms_eval/models/llama_vid.py) to install the model. And welcome to PR your models.

## Evaluation
Example:
model:  Video-LLaVA-7B
```
export OPENAI_API_KEY="XXXXX" (For open-ended evaluation)
```

```bash
accelerate launch --num_processes=8 --main_process_port 12345 -m lmms_eval \
    --model video_llava   \
    --model_args pretrained='LanguageBind/Video-LLaVA-7B' \
    --tasks worldqa  \
    --batch_size 1 \
    --log_samples \
    --log_samples_suffix debug\
    --output_path ./logs/
```
