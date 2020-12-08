# Super-Resolution Audio

DeciBull streams high quality audio i.e. super-resolution audio from the low quality audio transmitted from your device by using generative models such as General Adversarial networks (GANs)/Auto Encoders. This concept of generating super resolution audio is borrowed from successful use of GANs and AutoEncoders to generate super resolution images.
A GAN comprises of two models i.e. a generator and a discriminator model which are used to resolve missing details in images/audio to generate super resolution images/audio from low quality images. Although our work is heavily inspired from existing research on using GANs 
to generate super resolution audio, most of the research has been focused on generating batch high resolution audio. DeciBull attempts to use generative models to stream super resolution audio realtime.

<figure>
  <img src="/img/GAN_basic.PNG" width="600">
  <figcaption>Super-resolution Audio generation using GANs</figcaption>
</figure>
