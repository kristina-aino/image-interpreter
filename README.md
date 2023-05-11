# image-interpreter

## Features

### Model Functions
- provided with an image a set of models extracts the following meta informatioin from it:
  - depth
  - pose
  - segmentation
  - caption
- this additional information is given to a controlnet architecture to generate a new set of images from these abstract descriptions
- lastly a CLIP model evaluates the different generated images and their respective abstract structural inputs

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
