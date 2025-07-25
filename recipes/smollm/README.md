
# Instructions to train SmolLM-Instruct

We build the [SmolLM-Instruct](https://huggingface.co/collections/HuggingFaceTB/smollm-6695016cad7167254ce15966) (v0.2) models (135M, 360M and 1.7B) by doing SFT on a mix of these datasets:
- a dataset of 2k simple everyday conversations we generated by llama3.1-70B [everyday-conversations-llama3.1-2k](https://huggingface.co/datasets/HuggingFaceTB/everyday-conversations-llama3.1-2k/)
- [Magpie-Pro-300K-Filtered](https://huggingface.co/datasets/Magpie-Align/Magpie-Pro-300K-Filtered)
- [StarCoder2-Self-OSS-Instruct](https://huggingface.co/datasets/bigcode/self-oss-instruct-sc2-exec-filter-50k)
- A small subset of [OpenHermes-2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5)

## Setup

Follow the installation instructions in https://github.com/huggingface/alignment-handbook/tree/main?tab=readme-ov-file#installation-instructions 

## Training
We train the models on 8 GPUs using the following command:

```shell
ACCELERATE_LOG_LEVEL=info accelerate launch --config_file recipes/accelerate_configs/zero3.yaml scripts/sft.py --config recipes/smollm/sft/config.yaml
```
