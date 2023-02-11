# dreambooth-stablediffusion-sagemaker-notebook  
 
* Can be running on Jupyter Lab of Amazon SageMaker g4dn or g5 notebook instance(xlarge type is enough, 50GB volume size is good to go).
* Example codes for real-time inference and async inference can be found in g4dn notebook(g5 notebook, real-time inference only).
* Tested with Stable Diffusion v1.5 aka "runwayml/stable-diffusion-v1-5". And you can also use the model v2.0 & v2.1. But seemed that v1.5 gained the best results, maybe v2.0+ models need more steps for training, you can try those by yourself.
* In my practice, adding "prior-preservation loss" for "style" training has less impact to results. I keep same configurations just for consistency. You can try training without "prior-preservation loss" by yourself. More information about "training with prior-preservation loss", refer [here](https://github.com/huggingface/diffusers/tree/main/examples/dreambooth#training-with-prior-preservation-loss).  


> If you encounter error of "IsADirectoryError: [Errno 21] Is a directory: '/home/ec2-user/SageMaker/images/source/.ipynb_checkpoints" during training stage, you need to delete ".ipynb_checkpoints", then continue your training  

> If you encounter error of "CUDA out of memory..." during training stage, you can simply restart the kernel of Jupyter Notebook, then start your training from the begining

