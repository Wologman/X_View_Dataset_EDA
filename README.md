# EDA of the Xview satellite imagery dataset
A basic EDA of the Xview Satellite imagery dataset.  And reformatting code to create a YOLO and COCO formatted training dataset.

Dataset from [here](http://xviewdataset.org/)  This was the best benchmarking satellite machine vision dataset I could find at the time. [Paper here](https://arxiv.org/pdf/1802.07856.pdf), and a description of the dataset format [here](https://challenge.xviewdataset.org/data-format). The more recent Chinese one  [FARI1M](http://gaofen-challenge.com/) looked potentially better but was unavailable at the time.

Only 60% of the dataset is provided.  The competition organisers held back 20% for leaderboard, and 20% for private test set and they have never been released.  I was mainly interested in the vehicle categories, but I pre-trained a YOLO model on all categories to improve generalisation.

I used the included geoExplore_environment.yml for data exploration.  Usage: `conda env create -f geoExplore_environment.yml`

I have set up one notebook for data exploration explore_data.ipynb, and a second stand alone notebook to do some cleaning and re-format to YOLO format, with tiles and corresponding labels re-sized to any value.  

The tile size can be adjusted to anything.  To train a YOLOv5 model with 640x640 image tiles and a batch size of 8 took 3.1G of GPU memory on my laptop.

I performed the following basic cleaning steps in the formatting notebook:

- Removed labels refering to non-existant image 1385
- Removed labels refering to a erroneous categories 75 & 82
- Re-labelled all the class labels to have class-IDs from 0 to 59
