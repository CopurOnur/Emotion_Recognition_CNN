# Emotion Recognition

# Goal of the Project

Training a simple CNN on [FER2013](https://www.kaggle.com/msambare/fer2013) dataset for 7 basic emotion detection and explaining the behaviour of the model with [Lime](https://github.com/marcotcr/lime).

### The Datatset

- The data consists of 48x48 pixel grayscale images of faces. The faces have been automatically registered so that the face is more or less centred and occupies about the same amount of space in each image.
- The task is to categorize each face based on the emotion shown in the facial expression into one of seven categories (0=Angry, 1=Disgust, 2=Fear, 3=Happy, 4=Sad, 5=Surprise, 6=Neutral). The training set consists of 28,709 examples and the public test set consists of 3,589 examples.

![Untitled](Emotion%20Recognition%20c40e34f6b2ee4f7ba4249842e45c728b/Untitled.png)

### The Model

The CNN model we use is a simple CNN architecture composed of 4 blocks each with 2 convolutional layers, a batch normalization layer, max pooling layer and finally drop out. After the CNN blocks, a fully connected layer is used for 7 class classification. In total, there are 3,332,679 trainable and 1,024 non trainable parameters.

### Results

![Untitled](Emotion%20Recognition%20c40e34f6b2ee4f7ba4249842e45c728b/Untitled%201.png)

### Lime Interpretability

While treating the model as a black box, we perturb the instance we want to explain and learn a sparse linear model around it, as an explanation. The figure below illustrates the intuition for this procedure. The model's decision function is represented by the blue/pink background, and is clearly nonlinear. The bright red cross is the instance being explained (let's call it X). We sample instances around X, and weight them according to their proximity to X (weight here is indicated by size). We then learn a linear model (dashed line) that approximates the model well in the vicinity of X, but not necessarily globally.

![Untitled](Emotion%20Recognition%20c40e34f6b2ee4f7ba4249842e45c728b/Untitled%202.png)

Bellow you can see a correctly classified sample from each emotion label. There are 4 figures presented for each label, the first figure shows the original image, the second figure shows the super pixels contributing poisitively to the prediction in the rgb image format. In this, some samples looks dark because of converting from gray scale to rgb. The third figure in each sample shows the same pixels but this time the boundry of theese positively contributing pixels are marked on the gray scale image. Finally, the last figure shows the boundry of the pixels negatively contributing to the prediction of the label.

![Untitled](Emotion%20Recognition%20c40e34f6b2ee4f7ba4249842e45c728b/Untitled%203.png)

![Untitled](Emotion%20Recognition%20c40e34f6b2ee4f7ba4249842e45c728b/Untitled%204.png)