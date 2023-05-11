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
- Models
