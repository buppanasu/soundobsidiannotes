A **band-pass filter** allows frequencies within a specific range to pass through while attenuating frequencies outside that range. This can be useful when you want to isolate a certain frequency band, such as filtering out everything except a vocal range.


```shell
from scipy.signal import butter, lfilter

def butter_bandpass(lowcut, highcut, fs, order=5):
    nyquist = 0.5 * fs
    normal_lowcut = lowcut / nyquist
    normal_highcut = highcut / nyquist
    b, a = butter(order, [normal_lowcut, normal_highcut], btype='band', analog=False)
    return b, a

def bandpass_filter(data, lowcut, highcut, fs, order=5):
    b, a = butter_bandpass(lowcut, highcut, fs, order)
    return lfilter(b, a, data)

# Example usage of band-pass filter
lowcut = 500.0  # Example low frequency for band-pass
highcut = 3000.0  # Example high frequency for band-pass
data_int_filtered_band = bandpass_filter(data_int, lowcut, highcut, RATE)
yf = fft(data_int_filtered_band)

```

- **Explanation**:
    
    - **`butter_bandpass()`**: Designs a band-pass Butterworth filter with specified low (`lowcut`) and high (`highcut`) cutoff frequencies.
        
    - **`bandpass_filter()`**: Applies the band-pass filter to the audio data (`data`).