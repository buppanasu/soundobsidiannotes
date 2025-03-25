![[Pasted image 20250325214145.png]]

 
- **pyaudio.PyAudio()** initializes the PyAudio instance.
    
- The **stream** object is created using `audio.open()`, which configures the microphone to capture audio.
    
- The stream is set to read audio data from the microphone, and data will be collected in chunks of `BUFFER` samples.