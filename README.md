# dreambooth-stablediffusion-sagemaker-notebook  
 
* Can be running on Jupyter Lab of Amazon SageMaker g4dn or g5 notebook instance(xlarge type is enough, 50GB volume size is good to go, use kernel conda_python3).  
* Tested with Stable Diffusion v1.5 aka "runwayml/stable-diffusion-v1-5". And you can also use the model v2.0 & v2.1. But seemed that v1.5 gained the best results, maybe v2.0+ models need more steps for training, you can try those by yourself.  
* Regarding "Style/Object" training, refer to g4dn notebook. For "Person" training, check out g5 notebook. Since "training with prior-preservation loss" has less impact to "Style/Object" training, I removed codes of generating "class images" for prior-preservation loss in g4dn "style" training. More details for explaination, refer [here](https://github.com/huggingface/diffusers/tree/main/examples/dreambooth#training-with-prior-preservation-loss).  
* I used two different scripts for DreamBooth training just for making examples, [ShivamShrirao's repo](https://github.com/ShivamShrirao/diffusers/tree/main/examples/dreambooth) for g4dn, and [Huggingface's repo](https://github.com/huggingface/diffusers/tree/main/examples/dreambooth) for g5, recommend the first one no matter you use g4dn or g5, because it takes up less vram and less time for training.
* Example codes for real-time inference and async inference can be found in g4dn notebook(g5 notebook, real-time inference only).  
* There is a very good article which elaborate all kinds of parameters for DreamBooth fine tuning, read [the paper](https://github.com/d8ahazard/sd_dreambooth_extension/discussions/547) carefully before you modify the training scripts.

> If you encounter error of "IsADirectoryError: [Errno 21] Is a directory: '/home/ec2-user/SageMaker/images/source/.ipynb_checkpoints" during training stage, you need to delete ".ipynb_checkpoints", then continue your training  

> If you encounter error of "CUDA out of memory..." during training stage, you can simply restart the kernel of Jupyter Notebook, then start your training from the begining  

# sd-lora-db-finetune-sagemaker-notebook 
* Use [kohya-ss scripts](https://github.com/kohya-ss/sd-scripts) for Lora fine tuning, which is probably the most popular method for Lora training
* Example for person(character) trainingg using captions(aka filewords)

# lora_pti-stablediffusion-sagemaker-notebook  
* Adding Lora-PTI training for Stable Diffusion(a little bit under-fitting, needs more steps for training) just for fun. 
* Method comes from [cloneofsimo](https://github.com/cloneofsimo/lora), and the repo is a bit of inactive, so pls use kohya-ss method for Lora training

