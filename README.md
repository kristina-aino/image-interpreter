# image-interpreter

This project aims to provide the infrastructure, the environment and the functionality for generating images based on abstract information extracted from a sample picture.
Two Goals:
  1) Generate images based on priors from a variety of sources, and then selecting or editing those priors (like captions) to have more fine grained controll over image generation.
  2) Explore and compare different options for model deployment, the collection and recollection of data (local), finetuning, inference, speed and other architectural questions.
  3) Compare different models in performance, ability to generate and other relevant metrics

## Features

### Model Functions
- provided with an image a set of models extracts the following meta informatioin from it:
  - depth
  - pose
  - segmentation 
    - [sqeezenet](https://pytorch.org/hub/pytorch_vision_squeezenet/)
    - [SNNMLP](https://pytorch.org/hub/pytorch_vision_snnmlp/)
    - [FCN](https://pytorch.org/hub/pytorch_vision_fcn_resnet101/)
    - [densenet](https://pytorch.org/hub/pytorch_vision_densenet/)
    - [YOLOv5](https://pytorch.org/hub/ultralytics_yolov5/)
    - [Resnext WSL](https://pytorch.org/hub/facebookresearch_WSL-Images_resnext/)
    - [facebookresearch/segment-anything](https://github.com/facebookresearch/segment-anything)
  - caption ([Amazon Bedrock](https://aws.amazon.com/bedrock/?nc2=h_ql_prod_ml_br), )
  - more...
- this additional information is given to a set of controlnet's to generate a new image each from the abstract priors

### Deployment Functions
- All models are provided on [Hugginface](https://huggingface.co/) and should be downloaded once at initialization in a dedicated permanent storage, most likely cloud
- The backend loads and serves the different models, but i want to test the following frameworks:
  - [TorchServe](https://github.com/pytorch/serve/tree/master)
  - *in case of tensorflow models [TensorFlow Serve](https://www.tensorflow.org/tfx/guide/serving)*
  - [PyTorch on VertexAI](https://cloud.google.com/blog/topics/developers-practitioners/pytorch-google-cloud-how-deploy-pytorch-models-vertex-ai)
  - [Triton inference server](https://catalog.ngc.nvidia.com/orgs/nvidia/containers/tritonserver)
  - [BentoML](https://github.com/bentoml/bentoml)
  - [awslabs/multi-model-server](https://github.com/awslabs/multi-model-server)
  - [seldon](https://github.com/SeldonIO/seldon-core)
  - [clear-ml](https://github.com/allegroai/clearml)
  - [ml-flow](https://github.com/mlflow/mlflow)
  - my own flask REST API
- models should be available individually as well as in a pipeline
- There should be an interface for finetuning specific models, recording their progress and versioning.


### Further features
- The different informations extracted from the image should be combined at some point
- an interface to engage with generated images
- a CLIP model should be used to evaluate priors -> images mappings to compare and select different image samples by hand (both for generation at inference time and for collecting user data
- super resolution
- stable diffusion latent interpolation with some selected fixed point consistency (maybe in the priors, maybe apply to video)
- leverage conversational agents (e.g. [OpenAssistant](https://huggingface.co/OpenAssistant)) to help steer editing


### TODO
