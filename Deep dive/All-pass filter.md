An **all-pass filter** is a filter that passes all frequencies through, but with different phase shifts for different frequencies. These are not commonly used in basic audio processing but can be helpful in phase correction tasks.

```shell
from scipy.signal import butter, lfilter

def butter_allpass(cutoff, fs, order=5):
    nyquist = 0.5 * fs
    normal_cutoff = cutoff / nyquist
    b, a = butter(order, normal_cutoff, btype='allpass', analog=False)
    return b, a

def allpass_filter(data, cutoff, fs, order=5):
    b, a = butter_allpass(cutoff, fs, order)
    return lfilter(b, a, data)

# Example usage of all-pass filter
cutoff = 1000  # Example cutoff frequency for all-pass filter
data_int_filtered_allpass = allpass_filter(data_int, cutoff, RATE)
yf = fft(data_int_filtered_allpass)

```


- **Explanation**:
    
    - **`butter_allpass()`**: Designs an all-pass filter with the specified cutoff frequency and order.
        
    - **`allpass_filter()`**: Applies the all-pass filter to the audio data.