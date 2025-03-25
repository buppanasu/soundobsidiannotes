
- **Question**: "Modify the code to calculate and display the RMS value of the audio signal in real-time."
    
- **Expected Modification**: You can calculate the RMS value of the audio data using numpy:

```shell
rms = np.sqrt(np.mean(np.square(data_int)))
print(f'RMS Value: {rms}')

```