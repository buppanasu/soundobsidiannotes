
- **Question**: "Modify the code to save the recorded audio to a `.wav` file while recording."
    
- **Expected Modification**: After reading the audio data, save it as a `.wav` file using a library like `wave`. You'll need to set up a `wave.open()` object and write the audio data to the file.

```shell
import wave

# Open a .wav file for writing
output_file = wave.open('output.wav', 'wb')
output_file.setnchannels(CHANNELS)
output_file.setsampwidth(pyaudio.PyAudio().get_sample_size(FORMAT))
output_file.setframerate(RATE)

# Write the audio data to the file
output_file.writeframes(data)
output_file.close()

```