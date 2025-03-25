
- **Question**: "Modify the code to plot a **spectrogram** instead of a frequency spectrum in the second plot."
    
- **Expected Modification**: You can use `matplotlib`'s `specgram` function or `scipy.signal.spectrogram` to display the spectrogram. Replace the current FFT plot with the spectrogram plot:

```shell
from scipy.signal import spectrogram

# Calculate the spectrogram
f, t, Sxx = spectrogram(data_int, RATE)

# Update the second plot (frequency spectrum) to show the spectrogram
ax2.pcolormesh(t, f, 10 * np.log10(Sxx))
ax2.set_xlabel('Time [s]')
ax2.set_ylabel('Frequency [Hz]')
ax2.set_title('Spectrogram')
```