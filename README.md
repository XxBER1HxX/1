# Intro
Before I describe the details of the code, I want to share my thoughts on the task and explain why the work was not fully completed.
I'll be honest - I've never worked with this kind of task before, where there is no input data and you need to create scripts, Dockerfile, and so on. So it was interesting and really similar to a real task. Of course, I could have used tricks, copied other people's work or tried to fraudulently obtain the material, but "this is not it". I come to you to gain knowledge and I want to demonstrate my level of knowledge, not my level of copying or cheating. I think this will be fair (of course, it's a pity that I can't demonstrate my desire to learn as well as honesty). Time is also one of the reasons for incomplete realization. Ignoring the fact that the assignment says 72 hours, I am sending this now. Because today is the 19th and the registration deadline for your course is coming up and you might be making the final lists of participants. So, after this short preface, let's get to the code.

## Data 
To train the model, data is essential. However, for this task, we won't have access to real data due to certain limitations. Therefore, we will need to generate our own training data. Fortunately, we can utilize the EMNIST dataset since our objective involves identifying handwritten characters. You can find the detailed description of this dataset in the provided [reference.](https://www.tensorflow.org/datasets/catalog/emnist) 
To use the EMNIST dataset, we need to:
- Download the dataset [here](https://www.itl.nist.gov/iaui/vip/cs_links/EMNIST/gzip.zip)
- From inside the gzip folder, extract the following .gz files :
  - emnist-byclass-train-images-idx3-ubyte.gz
  - emnist-byclass-train-labels-idx1-ubyte.gz
  - emnist-byclass-test-images-idx3-ubyte.gz
  - emnist-byclass-test-labels-idx1-ubyte.gz
In short, why I chose EMNIST ByClass is because the dataset contains handwritten characters that are more representative of real-world scenarios than computer-generated or printed characters. This makes the dataset more suitable for tasks involving handwriting recognition and synthesis.

P.S. Most likely, the first hint is related to data generation. I will not take the second and third hints, because the first hint will be taken first and I will lose conditional points.

## Model
I made a convolutional neural network (CNN) model.

Configs
learning_rate = 0.001
train_epochs = 10
train_workers = 20
val_split = 0.2
batch_size = 200

The model is defined as a sequential model using `tf.keras.models.Sequential()`.
- It consists of several layers:
  - The first layer is a 2D convolutional layer (`Conv2D`) with 64 filters, a kernel size of 3x3, and ReLU activation. It takes the input shape of (28, 28, 1)
  - Next, a max-pooling layer (`MaxPool2D`) with a pool size of 2x2 is added to downsample the feature maps.
  - A dropout layer (`Dropout`) is included to prevent overfitting by randomly setting a fraction of input units to 0 during training.
  - The feature maps are then flattened into a 1D vector using the flatten layer (`Flatten`).
  - Two fully connected dense layers (`Dense`) follow: the first layer has 256 units with ReLU activation, and the last layer has 62 units (corresponding to the number of classes in EMNIST) with softmax activation for multi-class classification.

- Compilation and Training:
  - The model is compiled using the Adam optimizer with a specified learning rate.
  - The loss function is set to "sparse_categorical_crossentropy" since the labels are provided as integers.
  - The metric used to evaluate the model during training is accuracy.
  - The training and validation datasets are converted into TensorFlow datasets using `tf.data.Dataset.from_tensor_slices()` and batched.
  - The model is trained using the `fit` function, specifying the training and validation datasets, the number of epochs, and the number of workers for parallel processing.

## Result
The training results indicate that the model achieved a loss of 0.3345 and an accuracy of 0.8734 on the training data after 10 epochs. Additionally, on the validation data, the model achieved a validation loss of 0.4207 and a validation accuracy of 0.8520.

Based on these results, it seems that the model has learned to generalize well to the validation data. The training accuracy of 0.8734 indicates that the model is able to classify the training samples correctly with a high accuracy rate. The validation accuracy of 0.8520 suggests that the model is performing well on unseen data, which is a positive sign. Of course, with time and better computer power, you can change the parameters and achieve better results.

## Summary
To be honest, I doubt that anyone will ever reach this stage because nobody wants to invest time in an unfinished and incomplete task. I understand. Ultimately, all I can do is express my gratitude for the time you have dedicated to my assignment. Or maybe my knowledge is sufficient to be accepted into your courses. I am hopeful in this regard. Thank you!
