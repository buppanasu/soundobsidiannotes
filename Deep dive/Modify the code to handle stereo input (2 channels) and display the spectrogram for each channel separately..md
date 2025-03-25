- **Question**: "Modify the code to handle stereo input (2 channels) and display the spectrogram for each channel separately."
    
- **Expected Modification**: You will need to handle the two audio channels separately, performing FFT and displaying their spectrograms individually:

```shell
data_left, data_right = data_int[::2], data_int[1::2]  # Split stereo channels

# Perform FFT for each channel separately
yf_left = fft(data_left)
yf_right = fft(data_right)

```