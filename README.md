# image-interpreter

This project aims to provide functionality for generating images based on abstract information extracted from another image.

> The Idea:
> Given an image, there are a number of abstract paramerers describing that image.
> 
> The advancements in both text based image generation and pose-prior based image generation are both examples on how far this could go.
>
> The main Idea is to have two main components, a `extractor` and a `generator`
> - the `extractor` is meant to extract any level of information from an image, including but not limited to:
>   - image description (paritally and whole, i.e. object specific text queries)
>   - poses of humans in the scene
>   - facial expressions and hand gestures
> - Then the `generator` is tasked with generating another set of images from this abstract prior
> - An Interface between the two gives the user the option of picking and choosing the different priors, change them or ignoring them.
>
> Goal is to do classical image generation but give more finegrained controll
> over differing settings (similar to controll net or pose net) but
> increase semantic dependency and thus also (hopefully) increase output consistency.

## Features

### Model Functions (draft)
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

### Further features
- The different informations extracted from the image should be cross related to other latend loss functions
- a CLIP model should be used to evaluate priors -> images mappings to compare and select different image samples by hand (both for generation at inference time and for collecting user data
- super resolution
- stable diffusion latent interpolation with some selected fixed point consistency (maybe in the priors, maybe apply to video)
- leverage conversational agents (e.g. [OpenAssistant](https://huggingface.co/OpenAssistant)) to help steer editing

### TODO
