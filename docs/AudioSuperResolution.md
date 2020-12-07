# Audio Super-resolution

DeciBull streams high quality audio i.e. super-resolution audio from the low quality audio transmitted from your device by using General Adversarial networks (GANs). This concept of generating super resolution audio is borrowed from successful use of GANs to generate super resolution images.
A GAN comprises of two models i.e. a generator and a discriminator model which are used to resolve missing details in images/audio to generate super resolution images/audio from low quality images. Although our work is heavily inspired from existing research on using GANs 
to generate super resolution audio, most of the research has been focused on generating batch high resolution audio. DeciBull attempts to use GANs to stream super resolution audio realtime.

<figure>
  <img src="/img/GAN_basic.PNG" width="600">
  <figcaption>Super-resolution Audio generation using GANs</figcaption>
</figure>
