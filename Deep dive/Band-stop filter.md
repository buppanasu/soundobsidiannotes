
#### a. **Band-Stop Filter (Notch Filter)**

A **band-stop filter** (also known as a notch filter) blocks a specific range of frequencies while allowing others to pass. It’s essentially the inverse of a band-pass filter.

```shell
from scipy.signal import butter, lfilter

def butter_bandstop(lowcut, highcut, fs, order=5):
    nyquist = 0.5 * fs
    normal_lowcut = lowcut / nyquist
    normal_highcut = highcut / nyquist
    b, a = butter(order, [normal_lowcut, normal_highcut], btype='bandstop', analog=False)
    return b, a

def bandstop_filter(data, lowcut, highcut, fs, order=5):
    b, a = butter_bandstop(lowcut, highcut, fs, order)
    return lfilter(b, a, data)

# Example usage of band-stop filter
lowcut = 1500.0  # Example low frequency for band-stop
highcut = 2500.0  # Example high frequency for band-stop
data_int_filtered_bandstop = bandstop_filter(data_int, lowcut, highcut, RATE)
yf = fft(data_int_filtered_bandstop)

```

**Explanation**:

- **`butter_bandstop()`**: Designs a band-stop Butterworth filter with specified low and high cutoff frequencies.
    
- **`bandstop_filter()`**: Applies the band-stop filter to the audio data.