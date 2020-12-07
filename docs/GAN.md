# DeciBull Network Architecture
We use the traditional GAN architecture where the generator comprises of multiple fully connected neural net layers with relu activation function and the discriminator is a simple classification neural network to identify real vs generated high quality audio. DeciBull is trained on more than 80GB of high quality uncompressed speech data from multiple languages so that it can work for different speakers and dialects.

<figure>
  <img src="/img/gan_diagram.png" width="600">
  <figcaption>GAN architecture for DeciBull</figcaption>
</figure>

We train by compressing our high quality audio data to low quality for training with the target of generating the original high quality audio. Before pushing the low quality audio to the GAN network, we transform the audio waveform into frequency and time domain using a Fourier transform to generate a spectrogram. We then push audio amplitudes at different frequencies for 10ms audio chunks into the model to generate higher quality audio realtime. Applications such as Zoom stream audio at a bit depth of below 64k and Decibull generates audio to match a standardized 320k bit depth and 48k sampling rate.
