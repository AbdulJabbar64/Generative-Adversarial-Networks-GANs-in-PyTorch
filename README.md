# Generative-Adversarial-Networks-GANs-in-PyTorch
# Introduction to Generative Modeling
* Deep neural networks are used mainly for supervised learning: classification or regression. Generative Adversarial Networks or GANs, however, use neural networks for a very different purpose: Generative modeling
* Generative modeling is an unsupervised learning task in machine learning that involves automatically discovering and learning the regularities or patterns in input data in such a way that the model can be used to generate or output new examples that plausibly could have been drawn from the original dataset
* While there are many approaches used for generative modeling, a Generative Adversarial Network takes the following approach:
![alt text](https://github.com/AbdulJabbar64/Generative-Adversarial-Networks-GANs-in-PyTorch/blob/main/Images/GANs.png)

* There are two neural networks: a Generator and a Discriminator. The generator generates a "fake" sample given a random vector/matrix, and the discriminator attempts to detect whether a given sample is "real" (picked from the training data) or "fake" (generated by the generator). Training happens in tandem: we train the discriminator for a few epochs, then train the generator for a few epochs, and repeat. This way both the generator and the discriminator get better at doing their jobs.
* GANs however, can be notoriously difficult to train, and are extremely sensitive to hyperparameters, activation functions and regularization. We'll train a GAN to generate images of anime characters' faces.
![alt text](https://github.com/AbdulJabbar64/Generative-Adversarial-Networks-GANs-in-PyTorch/blob/main/Images/fake%20image.png)

# Generator Network
* The input to the generator is typically a vector or a matrix of random numbers (referred to as a latent tensor) which is used as a seed for generating an image. The generator will convert a latent tensor of shape (128, 1, 1) into an image tensor of shape 3 x 28 x 28. To achive this, we'll use the ConvTranspose2d layer from PyTorch, which is performs to as a transposed convolution (also referred to as a deconvolution). [Learn more](https://github.com/vdumoulin/conv_arithmetic/blob/master/README.md#transposed-convolution-animations)
![alt text](https://github.com/AbdulJabbar64/Generative-Adversarial-Networks-GANs-in-PyTorch/blob/main/Images/Generator%20Network.gif)

# Discriminator Training
* Since the discriminator is a binary classification model, we can use the binary cross entropy loss function to quantify how well it is able to differentiate between real and generated images. 
![alt text](https://github.com/AbdulJabbar64/Generative-Adversarial-Networks-GANs-in-PyTorch/blob/main/Images/Discriminator.jpg)

# Generator Training
Since the outputs of the generator are images, it's not obvious how we can train the generator. This is where we employ a rather elegant trick, which is to use the discriminator as a part of the loss function. Here's how it works:
* We generate a batch of images using the generator, pass the into the discriminator.
* We calculate the loss by setting the target labels to 1 i.e. real. We do this because the generator's objective is to "fool" the discriminator.
* We use the loss to perform gradient descent i.e. change the weights of the generator, so it gets better at generating real-like images to "fool" the discriminator.
[Generator Training Video](https://github.com/AbdulJabbar64/Generative-Adversarial-Networks-GANs-in-PyTorch/blob/main/Images/gans_training.mp4)


https://user-images.githubusercontent.com/49620759/154310395-746dd44a-b191-40cd-9a3c-bfa4466daea0.mp4



