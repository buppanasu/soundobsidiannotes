
![[Pasted image 20250325214235.png]]

- **stream.read(BUFFER)**: Reads raw audio data from the microphone as binary data.
    
- **struct.unpack()**: Converts the binary data into a list of 16-bit integers (`data_int`).
    
- **FFT Computation**:
    
    - The Fast Fourier Transform (FFT) is applied to the integer audio data (`data_int`) using `fft(data_int)`.
        
    - This produces a frequency spectrum (`yf`) representing the frequencies present in the audio.
        
- **Update Plots**:
    
    - The audio waveform plot (`ax1`) is updated by setting the `ydata` of `line` to `data_int`.
        
    - The frequency spectrum plot (`ax2`) is updated by setting the `ydata` of `line_fft` to the absolute values of the FFT output (`np.abs(yf[0:BUFFER//2])`).
        
    - `fig.canvas.draw()` and `fig.canvas.flush_events()` are called to render the updated plots.
        
- **Measure Execution Time**: The time taken for each FFT computation is measured and appended to the `exec_time` list.


---
## Detailed Explanation:

```shell
for _ in range(0, RATE // BUFFER * RECORD_SECONDS):
```

**Purpose**: This loop will run a certain number of times based on the `RATE`, `BUFFER`, and `RECORD_SECONDS` parameters.

- **`RATE`**: The number of samples per second (sample rate). In this case, it’s set to 44,100 samples per second, meaning the microphone captures 44,100 samples every second.
    
- **`BUFFER`**: The number of samples per frame. It’s set to 1024 * 16, which means each frame will contain 16,384 samples.
    
- **`RECORD_SECONDS`**: This is the total time to record in seconds (e.g., 30 seconds).
    
**How to understand it**:
- **`RATE // BUFFER`**: This gives how many frames (buffers) you can capture per second. So, dividing `RATE (44100)` by `BUFFER (16384)` gives you about `2.7` buffers per second.
    
- **`RATE // BUFFER * RECORD_SECONDS`**: The number of frames to record over the entire `RECORD_SECONDS`. So, if `RECORD_SECONDS` is 30, it would capture about `2.7 * 30 ≈ 81` frames in total.
    

**Example**:

- For a 30-second recording, the loop will run 81 times (since 44,100 samples per second / 16,384 samples per buffer ≈ 2.7 buffers per second, and 2.7 * 30 seconds = 81 iterations).

---

```shell
data = stream.read(BUFFER)
```

- **Purpose**: This line reads `BUFFER` number of audio samples from the microphone stream and stores them in `data`.
    
    - **`stream.read(BUFFER)`**: Reads `BUFFER` amount of raw audio data from the microphone.
        
    - The data is still in raw byte format.
        
    
    **Example**:
    
    - If `BUFFER = 16384`, this will read 16,384 raw audio samples from the microphone.

---
```shell
 data_int = struct.unpack(str(BUFFER) + 'h', data)
```

**Purpose**: Converts the raw binary data into a list of 16-bit integers. These integers represent the actual audio signal.

- **`struct.unpack()`**: It converts the raw byte data into a list of integers.
    
    - The `h` format code indicates that each sample is a 16-bit signed integer.
        
    - `str(BUFFER) + 'h'` ensures that the correct number of samples is unpacked, based on the `BUFFER` size.
        

**Example**:

- If `data` contains 16,384 raw bytes, `struct.unpack()` converts these bytes into 16,384 16-bit integer values. These integers represent the amplitude of the audio signal at each sample point.

---
```shell
    start_time = time.time()  # for measuring frame rate
    yf = fft(data_int)

```

- **Purpose**: This section performs the Fast Fourier Transform (FFT) to convert the audio signal from the time domain into the frequency domain.
    
    - **`time.time()`**: Records the current time to calculate how long the FFT operation takes (useful for performance measurement).
        
    - **`fft(data_int)`**: The FFT is applied to the audio data (`data_int`), converting the signal from the time domain (where you see the waveform) to the frequency domain (where you can see the different frequencies present in the signal).
        
    
    **Example**:
    
    - If the audio signal contains a pure tone (e.g., a 1000 Hz sine wave), the FFT will show a peak at 1000 Hz, indicating the presence of that frequency in the signal.

---
```shell
exec_time.append(time.time() - start_time)
```
**Purpose**: Calculates the time taken to perform the FFT and appends it to the `exec_time` list.

- **`time.time() - start_time`**: Measures the execution time of the FFT operation.
    
- **`exec_time.append()`**: Stores the time it took for each FFT computation in the list `exec_time`, which can later be used to analyze the performance of the FFT over time.

---
```shell
line.set_ydata(data_int)
```
**Purpose**: Updates the audio waveform plot with the new audio data (the raw time-domain data).

- **`line.set_ydata(data_int)`**: Updates the `ydata` of the `line` object (which represents the waveform plot) with the new audio data (`data_int`).
    

**Example**:

- The waveform plot now updates to show the new audio signal captured in the current frame.

---
```shell
 line_fft.set_ydata(2.0 / BUFFER * np.abs(yf[0:BUFFER // 2]))
```
**Purpose**: Updates the frequency spectrum plot with the FFT results.

- **`np.abs(yf[0:BUFFER // 2])`**: Extracts the positive frequencies from the FFT result and computes their magnitudes.
    
- **`2.0 / BUFFER`**: Scales the FFT results so that the magnitude is normalized based on the number of samples in the buffer.
    
- **`line_fft.set_ydata()`**: Updates the frequency spectrum plot with the magnitude of the frequencies.
    

**Example**:

- If the FFT identifies a 1000 Hz frequency, it will show a peak at 1000 Hz on the frequency spectrum plot.

---
```shell
    fig.canvas.draw()
    fig.canvas.flush_events()
```
- **Purpose**: These commands redraw and refresh the plots to update them with new data.
    
    - **`fig.canvas.draw()`**: Redraws the plot with the updated data (both waveform and spectrum).
        
    - **`fig.canvas.flush_events()`**: Forces the plot to update immediately, ensuring the visualization stays in sync with the data.
---
### Putting it All Together (Example):

Imagine you're recording audio for 30 seconds with a sample rate of 44,100 Hz, and each buffer has 16,384 samples.

- The loop will run approximately **81 times** (based on `RATE // BUFFER * RECORD_SECONDS`).
    
- Each time through the loop, the program:
    
    1. **Reads** a chunk of audio data (`BUFFER` samples).
        
    2. **Converts** the raw data into integers.
        
    3. **Performs an FFT** on that chunk of data to analyze its frequency content.
        
    4. **Updates the plots** with the new waveform and frequency spectrum in real-time.
        

After the loop finishes (after 30 seconds of audio), you’ll have real-time plots of both the **audio waveform** and its **frequency spectrum** that updated continuously throughout the recording process.
