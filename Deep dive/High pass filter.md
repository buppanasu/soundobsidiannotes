

A **high-pass filter** allows frequencies above a certain cutoff to pass through and attenuates lower frequencies. The implementation is quite similar to the low-pass filter, but we set the `btype` to `'high'`.

```shell
from scipy.signal import butter, lfilter

def butter_highpass(cutoff, fs, order=5):
    nyquist = 0.5 * fs
    normal_cutoff = cutoff / nyquist
    b, a = butter(order, normal_cutoff, btype='high', analog=False)
    return b, a

def highpass_filter(data, cutoff, fs, order=5):
    b, a = butter_highpass(cutoff, fs, order)
    return lfilter(b, a, data)

# Example usage of high-pass filter
cutoff = 1000  # Example cutoff frequency for high-pass filter
data_int_filtered_high = highpass_filter(data_int, cutoff, RATE)
yf = fft(data_int_filtered_high)
```

- **Explanation**:
    
    - **`butter_highpass()`**: Designs a high-pass Butterworth filter with the specified cutoff frequency (`cutoff`), sample rate (`fs`), and order of the filter (`order`).
        
    - **`highpass_filter()`**: Applies the high-pass filter to the audio data (`data`) using the coefficients `b` and `a` returned by `butter_highpass()`.