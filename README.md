
# Create conda environment and package Installation

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

# Create face_encodings for faces in `known_images`

```sh
python prepare_reference_encodings.py -i "known_images/"
python prepare_reference_encodings.py -i "known_images/" --use-large-model

python prepare_reference_encodings.py -i "known_images/" --use-cvlib
python prepare_reference_encodings.py -i "known_images/" --use-cvlib --use-large-model
```

# To run the face recoginition

```sh
# On image
python recognize_face.py -t 0.5 -i "test_img.jpg" [--use-cvlib] [--use-large-model]

# On video
python recognize_face_in_video.py -t 0.5 [--use-cvlib] [--use-large-model]
```
