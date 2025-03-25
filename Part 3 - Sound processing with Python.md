1. Installing necessary Python libraries (may need additional libraries if not preinstalled with default python):

```shell
sudo apt install portaudio19-dev
pip3 install pyaudio
pip3 install sounddevice
pip3 install scipy matplotlib
```
[[What is a must have library to record audio stream from microphone?]]

After installation:
2. We capture the audio in Python. So beforehand the arecord and aplay is just used for testing
3. Next, we do Fourier transform ([[What is Fourier transform?]])
4. Visualize the sound waves (both the wave itself and the audio spectrum)


---
To do the tasks above, we can use these links:
- [sample code](https://github.com/drfuzzi/INF2009_SoundAnalytics/blob/main/Codes/microphone_streaming_with_spectrum.py) if you are using `_pyaudio_`.
- [sample code](https://github.com/drfuzzi/INF2009_SoundAnalytics/blob/main/Codes/microphone_streaming_with_spectrum_updated.py) if you are using `_sounddevice_`.

My Github link: 


---
Once we are done with sound processing, we have the processed sound already, we can move on to sound analytics:
[[Part 4 - Basic Sound Analytics]]