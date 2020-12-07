# How it works

DeciBull streams high quality audio i.e. super-resolution audio from the low quality audio transmitted from your device by using General Adversarial networks (GANs). This concept of generating super resolution audio is borrowed from successful use of GANs to generate super resolution images.
A GAN comprises of two models i.e. a generator and a discriminator model which are used to resolve missing details in images/audio to generate super resolution images/audio from low quality images. Although our work is heavily inspired from existing research on using GANs 
to generate super resolution audio, most of the research has been focused on generating batch high resolution audio. DeciBull attempts to use GANs to stream super resolution audio realtime.

<figure>
  <img src="/img/GAN_basic.PNG" width="600">
  <figcaption>Super-resolution Audio generation using GANs</figcaption>
</figure>

We use the traditional GAN architecture where the generator comprises of multiple fully connected neural net layers with relu activation function and the discriminator is a simple classification neural network to identify real vs generated high quality audio. DeciBull is trained on more than 80GB of high quality uncompressed speech data from multiple languages so that it can work for different speakers and dialects.

<figure>
  <img src="/img/gan_diagram.png" width="600">
  <figcaption>GAN architecture for DeciBull</figcaption>
</figure>

We train by compressing our high quality audio data to low quality for training with the target of generating the original high quality audio. Before pushing the low quality audio to the GAN network, we transform the audio waveform into frequency and time domain using a Fourier transform to generate a spectrogram. We then push audio amplitudes at different frequencies for 10ms audio chunks into the model to generate higher quality audio realtime. Applications such as Zoom stream audio at a bit depth of below 64k and Decibull generates audio to match a standardized 320k bit depth and 48k sampling rate.
We evaluate our generated audio on two metrics: (1) Square of differences, (2) Bit error rate.

Our first evaluation metric just evaluates how close the two audio signals (generated vs original high quality audio) are by comparing the raw waveforms at each audio sample and taking the square of differences of the two data points. 

<figure>
  <img src="/img/square_diff.PNG" width="400">
  <figcaption>Comparing square differences of two audio waveforms</figcaption>
</figure>


We also evaluate our audio samples using a more sophisticated methodology by creating an Audio Fingerprint of each audio file. The concept is similar to how apps like Shazam identify songs. Each song has a unique energy sequence at different frequency and time domain and can be given a unique fingerprint using these energy sequence. In our scenario we hash each of these energy values to bits and then compare the overall bit error rate between two audio files. To hash an audio file we convert the audio file into fingerprint blocks and then within each fingerprint block we segment our audio into frequency bands. For each frequency band in a single frame (time window) of audio, we then compute the energy and then hash them into bits by comparing neighbouring energy values. Once we have computed these bits for each frame, we then compare the bits at each frequency and time domain to get the bit errors. Image below shows the audio fingerprints for high quality and low quality files for same audio.


<figure>
  <img src="/img/fingerprint_example.png" width="400">
  <figcaption>Comparing fingerprints for low vs high quality audio</figcaption>
</figure>

Our model is integrated with an electron GUI that can be integrated with your audio device by changing the output of audio. This will stream your low quality audio to high quality generated audio to improve your online calling experience. 

[See DeciBull in Action](Examples){: .md-button }