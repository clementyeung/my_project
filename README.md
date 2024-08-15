# garbage_classification

Garbage_classificatin is a model that uses imagenet to classify garbage. It is capable of sorting 8 classes, battery, biological, cardboard, glass, paper, plastic and trash respectively. 

Here is an example output of garbage_classification:

![testtrash](https://github.com/user-attachments/assets/45111ebf-4255-4325-9ede-1e4928877585)

## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

It uses a retrained version of resnet18 to identify different types of garbage and classify them using imagenet.

## Running this project

Training the model: 
  1. Download all the files in the directory 
  2. Make sure to include any required libraries that need to be installed for your project to run.
  3. cd into jetson inference
  4. Run the following command in the termial when it is still in jetson_inference:
     echo 1 | sudo tee /proc/sys/vm/overcommit_memory
  5. Run the following command in the termial when it is still in jetson_inference: 
      ./docker/run.sh
  6. cd into jetson-inference/python/training/classification while you are in the docker
  7. python3 train.py --model-dir=models/garbage_classification data/garbage_classification

Downloading the model after you trained it: 
1. The model you trained should be located in jetson-inference/python/training/classification/models/garbage classification and the model should resnet18.onnx
2. press Ctrl + D to leave the docker
3. cd into jetson-inference/python/training/classification
4. use ls models/garbage_classification/ to ensure that the model is within the jetson nano
5. Run the following command in the terminal:
     NET=models/garbage_classification
     DATASET=data/dataset

Using the the pre-trained model: 
1. cd into jetson-inference/python/training/classification
2. Run the following commands in the terminal:
     NET=models/garbage_classification
     DATASET=data/dataset
3. Run imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/battery/battery_1.jpg test_battery_01.jpg
4. After the code finished running, you should find test_battery_01.jpg in the classification folder


[View a video explanation here](video link)
