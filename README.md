# Face Generator using GANs (Generative Adversarial Networks)
Model that alternatively trains a Discriminator with fake and real images and at the same time trains a Generator to create realistic faces.

![Image](https://github.com/jb-apps/gan-face-generation/blob/main/assets/face_generator.png)

# Data
Dataset provideda at [ CelebFaces Attributes Dataset (CelebA)](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)

# Architecture
The project mainly consists of two parts:
### Discriminator training:
We will train a Discriminator CNN with real images and with fake-generated images from the Generator then we use the combined loss from the fake and real images to do backpropagation on the Discriminator.

| Discriminator |
|---------------|
|![Image](https://github.com/jb-apps/gan-face-generation/blob/main/assets/conv_discriminator.png)|

### Generator training:
The Generator will be getting better at generating fake images as we will use a latent vector to generate fake images, then we feed it to the Discriminator.
As we want to fool the discriminator we will assume this fake images to be real. Then we do backpropagation to update the weights in the Generator.

| Generator |
|-----------|
|![Image](https://github.com/jb-apps/gan-face-generation/blob/main/assets/conv_generator.png)|

# Results
| Losses - 50 epoch|
|-----------|
|![](https://github.com/jb-apps/gan-face-generation/blob/main/assets/training_results.png)|

As this is a unsupervised method our losses will look different to a supervised one. However, the important take away from this graph is that the losses are stable in time. We can see some spikes in the Generator, this could mean it struggles to generate realistic faces because the images are pretty small (32x32).
However, the discriminator seems to be doing just fine as the loss at the beginning is going down, then it stabilises.
We could keep further training the network.

| Fake Generated Images! |
|-----------|
|![Fake Images](https://github.com/jb-apps/gan-face-generation/blob/main/assets/fake_images.png)|