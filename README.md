
## Setup

```sh
conda create -n ai python=3.8 numpy
conda activate ai
```

```sh
pip install cvlib
conda install -c conda-forge opencv
conda install -c anaconda tensorflow-gpu
conda install -c conda-forge face_recognition
```

## Prepare face encodings for faces in `known_images`

* Prepare the reference encodings where the input folder (`-i`) contains the folders of each individual
    - Create a folder containing the images of the person and place it under `known_images` folder
* face-recognition module has 2 different models
    1. Small model: Extract 5 feature points from the face and encode them
    2. Large model: Extract 58 feature points from the face and encode them


```sh
# Prepare the encodings for each face in every subfolder of known_images using small model
python prepare_reference_encodings.py -i "known_images/"
# Prepare the encodings for each face in every subfolder of known_images using large model
python prepare_reference_encodings.py -i "known_images/" --use-large-model

# Prepare the encodings for each face (detected using cvlib module) in every subfolder of known_images using small model
python prepare_reference_encodings.py -i "known_images/" --use-cvlib
# Prepare the encodings for each face (detected using cvlib module) in every subfolder of known_images using large model
python prepare_reference_encodings.py -i "known_images/" --use-cvlib --use-large-model
```

## Run the face recoginition application

```sh
# On image
python recognize_face.py -t 0.5 -i test/test4.jpg
python recognize_face.py -t 0.5 -i test/test4.jpg --use-large-model

python recognize_face.py -t 0.5 -i test/test4.jpg --use-cvlib
python recognize_face.py -t 0.5 -i test/test4.jpg --use-cvlib --use-large-model

# On video
python recognize_face_in_video.py -t 0.5
python recognize_face_in_video.py -t 0.5 --use-large-model

python recognize_face_in_video.py -t 0.5 --use-cvlib
python recognize_face_in_video.py -t 0.5 --use-cvlib --use-large-model

```
