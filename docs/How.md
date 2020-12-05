# How it works

We stream high quality audio i.e. super-resolution audio from the low quality audio from your device by using General Adversarial networks (GANs). This concept of generating super resolution audio is borrowed from generating super resolution images using GANs.
A GAN comprises of two models i.e. a generator and a discriminator model which are used to resolve missing details in images/audio to generate super resolution images/audio from low quality images. Although our work is heavily inspired from existing research on using GANs 
to generate super resolution audio, most of the research has been focused on generating batch high resolution audio. In our approach we are attempting to stream real time super resolution audio using GANs.

![GAN](img/GAN_basic.png)

