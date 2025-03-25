- **Question**: "Modify the code to highlight the spectral peaks (the dominant frequencies) in the frequency spectrum plot."
    
- **Expected Modification**: After performing the FFT, you could find the peaks in the frequency spectrum and highlight them:
```shell
peaks = np.argsort(np.abs(yf))[::-1][:5]  # Get the indices of the top 5 peaks
peak_freqs = xf[peaks]
peak_magnitudes = np.abs(yf[peaks])

ax2.plot(peak_freqs, peak_magnitudes, 'ro')  # Plot the peaks in red
```