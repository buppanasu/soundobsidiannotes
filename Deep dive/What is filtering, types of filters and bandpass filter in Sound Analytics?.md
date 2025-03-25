- Filtering: Removing noise or specific frequencies. The example code illustrates a bandpass filter (only passes audio within a certain frequencies as decided by the user are kept).

---
## Filtering: Removing Noise or specific frequencies
**Filtering** is a signal processing technique used to remove or enhance specific parts of a signal, such as noise or particular frequencies. In audio processing, this is commonly used to clean up signals, isolate important parts of the signal, or emphasize certain frequency ranges for analysis or listening.

When you capture audio, the signal may contain unwanted elements, like background noise, hum, or frequencies outside the desired range (such as high-frequency noise or low-frequency rumble). **Filtering** allows you to control which parts of the signal are kept or removed based on their frequency content.

---
## Types of filters
There are different types of filters, each designed to target specific frequencies in a signal. These include:

1. **Low-Pass Filter**:
    
    - This filter allows frequencies **below a certain cutoff frequency** to pass through while attenuating (reducing) frequencies above that cutoff.
        
    - Commonly used to remove high-frequency noise, such as hiss or static.
        
2. **High-Pass Filter**:
    
    - This filter allows frequencies **above a certain cutoff frequency** to pass through while attenuating frequencies below that cutoff.
        
    - It is often used to remove low-frequency noise, like rumble or hum.
        
3. **Band-Pass Filter**:
    
    - A **Band-Pass Filter** allows frequencies **within a specific range** (the "band") to pass through while attenuating frequencies **outside** of that range (both lower and higher frequencies).
        
    - This filter is useful when you want to focus on a particular frequency range and remove unwanted noise or interference from other parts of the spectrum.

---
### Band pass filter in detail

A **Band-Pass Filter** is a combination of a **low-pass** and a **high-pass** filter. It passes frequencies within a certain range while rejecting frequencies outside that range. This range is defined by two parameters: the **lower cutoff frequency** and the **upper cutoff frequency**.

For example:

- If you want to focus on speech, you may choose a frequency range between 300 Hz and 3,000 Hz (which typically encompasses human speech). Frequencies below 300 Hz (like background rumble) and above 3,000 Hz (like high-pitched noise) would be filtered out.
    

The **parameters** you define when setting up a band-pass filter are:

- **Lower cutoff frequency (f₁)**: The minimum frequency that the filter will allow.
    
- **Upper cutoff frequency (f₂)**: The maximum frequency that the filter will allow.
    
- The frequencies between **f₁** and **f₂** pass through, while everything below **f₁** and above **f₂** gets attenuated.

