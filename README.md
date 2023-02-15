# dreambooth-stablediffusion-sagemaker-notebook  
 
* Can be running on Jupyter Lab of Amazon SageMaker g4dn or g5 notebook instance(xlarge type is enough, 50GB volume size is good to go, use kernel conda_python3).  
* Tested with Stable Diffusion v1.5 aka "runwayml/stable-diffusion-v1-5". And you can also use the model v2.0 & v2.1. But seemed that v1.5 gained the best results, maybe v2.0+ models need more steps for training, you can try those by yourself.  
* Regarding "Style/Object" training, refer to g4dn notebook. For "Person" training, check out g5 notebook. Since "training with prior-preservation loss" has less impact to "Style/Object" training, I removed codes of generating "class images" for prior-preservation in g4dn "style" training. More details for explaination, refer [here](https://github.com/huggingface/diffusers/tree/main/examples/dreambooth#training-with-prior-preservation-loss).  
* Example codes for real-time inference and async inference can be found in g4dn notebook(g5 notebook, real-time inference only).  

> If you encounter error of "IsADirectoryError: [Errno 21] Is a directory: '/home/ec2-user/SageMaker/images/source/.ipynb_checkpoints" during training stage, you need to delete ".ipynb_checkpoints", then continue your training  

> If you encounter error of "CUDA out of memory..." during training stage, you can simply restart the kernel of Jupyter Notebook, then start your training from the begining

