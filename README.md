# Intro
Before I describe the details of the code, I want to share my thoughts on the task and 111, the thought process, etc. To be honest, I haven't worked with this kind of task where there is no data and you need to save the model, dockerfile, scripts in separate files, so it looked quite interesting and really similar to a real task. (If you are interested, I used to do tasks at DataCamp or university assignments). Looking ahead, I am satisfied with the work, the model has an accuracy of 85%. It's worth noting that I tried to complete the task as quickly as possible, despite the 72-hour deadline. Because today is the 19th, the deadline for registrations for your course, and it is quite possible that you will form the final lists of participants today. So, now that I've made myself as boring as possible, let's move on to the code.

## Data 
To train the model, we need data, of course. For obvious reasons, we won't be given real data for this task, so we need to generate training data. Since we will be dealing with the identification of handwritten characters, we can use the EMNIST dataset. The description of this dataset can be found at reference https://www.tensorflow.org/datasets/catalog/emnist .
To use the EMNIST dataset, you do not need to:
Download the dataset here [here](https://www.itl.nist.gov/iaui/vip/cs_links/EMNIST/gzip.zip)
From inside the gzip folder, extract the following .gz files :
- emnist-byclass-train-images-idx3-ubyte.gz
- emnist-byclass-train-labels-idx1-ubyte.gz
- emnist-byclass-test-images-idx3-ubyte.gz
- emnist-byclass-test-labels-idx1-ubyte.gz
If we briefly describe why emnist-byclass is used, then 333333
P.S Most likely, the first hint is related to data generation. I will not take the 2nd and 3rd hints, because I will lose conditional points for taking the first hint, which I do not need.

## Model.
