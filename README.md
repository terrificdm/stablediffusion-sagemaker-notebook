# How to use
* You don't need to git clone the whole repo, just pick up notebook which you want to use and download it to your local computer then upload to SageMaker notebook. RUN codes to go.  

-----------------------------------------------------------------------------------  
## SD model 1.x/2.x  

### dreambooth fine tuning series notebooks  
 
* Can be running on Jupyter Lab of Amazon SageMaker g4dn or g5 notebook instance(xlarge type is enough, 50GB volume size is good to go, use kernel conda_python3).  
* Tested with Stable Diffusion v1.5 aka "runwayml/stable-diffusion-v1-5". And you can also use the model v2.0 & v2.1. But seemed that v1.5 gained the best results, maybe v2.0+ models need more steps for training, you can try those by yourself.  
* Regarding "Style/Object" training, refer to g4dn notebook(also add character training with captions). For "Character/Person" training, check out g5 notebook. Since "training with prior-preservation loss" has less impact to "Style/Object" training, I removed codes of generating "class images" for prior-preservation loss in g4dn "style" training. More details for explaination, refer [here](https://github.com/huggingface/diffusers/tree/main/examples/dreambooth#training-with-prior-preservation-loss).  
* I used two different scripts for DreamBooth training just for making examples, [ShivamShrirao's repo](https://github.com/ShivamShrirao/diffusers/tree/main/examples/dreambooth) for g4dn, and [Huggingface's repo](https://github.com/huggingface/diffusers/tree/main/examples/dreambooth) for g5, recommend the first one no matter you use g4dn or g5, because it takes up less vram and less time for training.
* Example codes for real-time inference and async inference can be found in g4dn notebook(g5 notebook, real-time inference only).  
* There is a very good article which elaborate all kinds of parameters for DreamBooth fine tuning, read [the paper](https://github.com/d8ahazard/sd_dreambooth_extension/discussions/547) carefully before you modify the training scripts.

> If you encounter error of "IsADirectoryError: [Errno 21] Is a directory: '/home/ec2-user/SageMaker/images/source/.ipynb_checkpoints" during training stage, you need to delete ".ipynb_checkpoints", then continue your training  

> If you encounter error of "CUDA out of memory..." during training stage, you can simply restart the kernel of Jupyter Notebook, then start your training from the begining  

### Lora fine tuning series notebooks  
* Use [kohya-ss scripts](https://github.com/kohya-ss/sd-scripts) for Lora fine tuning, which is probably the most popular method for Lora training
* Examples are character(person) & style trainingg using captions(aka filewords), also add identifier+class method for style training(a bit of under-fitting)
* Training outputs(xxxx.safetensors) can be used directly for sdwebui
* Check captions of image dataset before you prepare yours, trigger word for character is "wta"  

### sd-classic-finetune-text2image-notebook
* Classtic fine tuning(aka native text2image fine tuning) example
* Including multi-gpu training on ml.g5.12xlarge SageMaker notebook instance, which which provides 4 NVIDIA A10G GPUs for parallelized(distributed) training
  
### sd-classic-finetune-text2image-decoupled-notebook
* Similar to "sd-classic-finetune-text2image-notebook", but use SageMaker trining job to decouple pre-processing stage and training stage  
* Very useful if full model fine tuning will take a long time, and you want to release training resource right after the training, which will save cost

-----------------------------------------------------------------------------------  

## SDXL model  
