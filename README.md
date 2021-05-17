# Swimming Detector

An object detector that can recognize what swimming stroke is being performed from an image. The detector was trained on a dataset that I collected.

### Data

Download the data from my [Kaggle](www.kaggle.com/dataset/3122f8d0287f6094b28d66e36b216b3a278eae858b6c7cb10f821010825397a2) repository. Additional images can be added first by downsizing using transform_image_resolution.py and labeled using [labelImg](https://github.com/tzutalin/labelImg). The data from Kaggle comes with the CSVs already made. Adding additional data will create new XML files that have to be converted to CSV using xml_to_csv.py. Image transformation and xml to csv scripts come from Gilbert Tanners [Creating your own object detector](https://towardsdatascience.com/creating-your-own-object-detector-ad69dda69c85) post on towards data science.

### Label Map

The labelmap.pbtxt file contains the information on the classes. There are four classes one for each stroke: freestyle, backstroke, butterfly, and breaststroke. Below is the example for freestyle.

```
item {
    name: "freestyle"
    id: 1
}
```

### Notebook

The uploaded file contains a notebook that train and run the model (I also included the notebook as a Python script in case that is easier to run). The notebook is from the tutorial made by Hugo Zanini on the [TensorFlow Blog](https://blog.tensorflow.org/2021/01/custom-object-detection-in-browser.html). I tweaked the number of classes, learning parameters, training length, and batch size for best results. All those values are already set up in the notebook.

### Running

I ran the notebook in Google Colab. Running in Colab gives access to GPUs and the download speeds to Colab are significantly faster than to my local machine.

The notebook first clones TensorFlow object detection, converts proto files to python, and downloads data from Kaggle if it is not already present. The labelmap is used to convert the training and testing photos to .record files. Once everything is setup the notebook will train and evaluate the model. A few image test images for reference are included at the bottom.

### Results

The results folder contains two screenshots of accuracy information from testing. First I trained the model to 7,000 then evaluated the progress to make sure everything worked properly. Then I let the model train until 10,000 steps and evaluated again. That is equivalent to approximately 4 hours of training in Google Colab. The results folder also contains the images that are in the paper.

### Thanks
Huge thanks to the [TensorFlow Blog](https://blog.tensorflow.org/2021/01/custom-object-detection-in-browser.html) post. I could not have done this project without all the super helpful explanations there.
