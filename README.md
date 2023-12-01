# Llama-2-ko-7B-GGUF
Llama-2-ko-gguf serves as an advanced iteration of Llama-2 expanded vocabulary of korean corpus


# 💻MAC os Compatible💻

# Llama 2 ko 7B - GGUF
- Model : [Llama 2 ko 7B gguf](https://huggingface.co/24bean/Llama-2-ko-7B-GGUF/)
- Model creator: [Meta](https://huggingface.co/meta-llama)
- Original model: [Llama 2 7B](https://huggingface.co/meta-llama/Llama-2-7b-hf)
- Original Llama 2 Ko model: [Llama 2 ko 7B](https://huggingface.co/beomi/llama-2-ko-7b)
- Reference: [Llama 2 7B GGUF](https://huggingface.co/TheBloke/Llama-2-7B-GGUF)
  
<!-- description start -->
## Download
```shell
pip3 install huggingface-hub>=0.17.1
```

Then you can download any individual model file to the current directory, at high speed, with a command like this:

```shell
huggingface-cli download 24bean/Llama-2-7B-ko-GGUF llama-2-ko-7b_q8_0.gguf --local-dir . --local-dir-use-symlinks False
```

Or you can download llama-2-ko-7b.gguf, non-quantized model by

```shell
huggingface-cli download 24bean/Llama-2-7B-ko-GGUF llama-2-ko-7b.gguf --local-dir . --local-dir-use-symlinks False
```

## Example `llama.cpp` command

Make sure you are using `llama.cpp` from commit [d0cee0d36d5be95a0d9088b674dbb27354107221](https://github.com/ggerganov/llama.cpp/commit/d0cee0d36d5be95a0d9088b674dbb27354107221) or later.

```shell
./main -ngl 32 -m llama-2-ko-7b_q8_0.gguf --color -c 4096 --temp 0.7 --repeat_penalty 1.1 -n -1 -p "{prompt}"
```

# How to run from Python code

You can use GGUF models from Python using the [llama-cpp-python](https://github.com/abetlen/llama-cpp-python) or [ctransformers](https://github.com/marella/ctransformers) libraries.

## How to load this model from Python using ctransformers

### First install the package

```bash
# Base ctransformers with no GPU acceleration
pip install ctransformers>=0.2.24
# Or with CUDA GPU acceleration
pip install ctransformers[cuda]>=0.2.24
# Or with ROCm GPU acceleration
CT_HIPBLAS=1 pip install ctransformers>=0.2.24 --no-binary ctransformers
# Or with Metal GPU acceleration for macOS systems
CT_METAL=1 pip install ctransformers>=0.2.24 --no-binary ctransformers
```

### Simple example code to load one of these GGUF models

```python
from ctransformers import AutoModelForCausalLM

# Set gpu_layers to the number of layers to offload to GPU. Set to 0 if no GPU acceleration is available on your system.
llm = AutoModelForCausalLM.from_pretrained("24bean/Llama-2-ko-7B-GGUF", model_file="llama-2-7b_q8_0.gguf", model_type="llama", gpu_layers=50)

print(llm("AI is going to"))
```

## How to use with LangChain

Here's guides on using llama-cpp-python or ctransformers with LangChain:

* [LangChain + llama-cpp-python](https://python.langchain.com/docs/integrations/llms/llamacpp)
* [LangChain + ctransformers](https://python.langchain.com/docs/integrations/providers/ctransformers)
