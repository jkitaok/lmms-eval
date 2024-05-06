# WorldQA Evaluation

To evaluate worldqa, the process is the same as evaluating the image dataset.

You can use
- video_llava
- llama_vid

You should first install `lmms-eval` using this branch and then follow the instructions in the `model` folder for [`video_llava`](https://github.com/EvolvingLMMs-Lab/lmms-eval/blob/kc/worldqa/lmms_eval/models/video_llava.py) and [`llama_vid`](https://github.com/EvolvingLMMs-Lab/lmms-eval/blob/kc/worldqa/lmms_eval/models/llama_vid.py) to install the model.

Then, you can run worldqa.

Example : 
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

You would also need to set your `OPENAI_API_KEY` in your environment for evaluation.
