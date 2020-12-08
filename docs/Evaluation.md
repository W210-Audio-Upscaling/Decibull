# Audio Quality Evaluation

Evaluation of audio quality is very important to understand how good or bad our generated audio is. Human ears are very sharp in identifying any background noise or disturbance in audio quality. However for DeciBull we wanted to comeup with more automated metrics that can help us evaluate our model output. We evaluate our generated audio on two metrics: (1) Square of differences (2) Bit error rate

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