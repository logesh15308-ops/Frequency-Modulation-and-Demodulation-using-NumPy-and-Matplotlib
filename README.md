# Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib
### AIM
    To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries.   
### APPARATUS REQUIRED
1.	Software: Python with NumPy and Matplotlib libraries  
2.	Hardware: Personal Computer  
### THEORY 
Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier wave is varied according to the instantaneous amplitude of the message signal. The general form of an FM signal is:


<img width="508" height="200" alt="image" src="https://github.com/user-attachments/assets/d69f6e8c-de84-4ee7-886b-0dc349407e29" />


### ALGORITHM

1.	Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and frequency deviation.    
2.	Generate Time Axis: Create a time vector for the signal duration.  
3.	Generate Message Signal: Define the message signal as a cosine wave.  
4.	Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.  
5.	Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.  
6.	Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

### PROGRAM
import numpy as np

import matplotlib.pyplot as plt

from scipy.signal import hilbert

Ac = 17 

Am = 8.5   

fc = 2189  

fm = 218.9 

fs = 21300  

kp = np.pi / 4 


t = np.arange(0, 2/fm, 1/fs)

m = Am * np.cos(2 * np.pi * fm * t)

c = Ac * np.cos(2 * np.pi * fc * t)

s = Ac * np.cos(2 * np.pi * fc * t + kp * m)

analytic_signal = hilbert(s)

inst_phase = np.unwrap(np.angle(analytic_signal))

m_demod = (inst_phase - 2 * np.pi * fc * t) / kp

m_demod = m_demod - np.mean(m_demod)  

plt.figure(figsize=(10, 8))

plt.subplot(4, 1, 1)

plt.plot(t, m, color='blue')

plt.title('Message Signal

plt.xlabel('Time (s)')

plt.ylabel('Amplitude (V)')

plt.subplot(4, 1, 2)

plt.plot(t, c, color='orange')

plt.title('Carrier Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude (V)')

plt.subplot(4, 1, 3)

plt.plot(t, s, color='green')

plt.title('Phase Modulated (PM) Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude (V)')

plt.subplot(4, 1, 4)

plt.plot(t, m_demod, color='red')

plt.title('Demodulated (Recovered) Signal')

plt.xlabel('Time (s)')

plt.ylabel('Amplitude (V)')

plt.tight_layout()

plt.show()

### TABULATION
![WhatsApp Image 2025-11-20 at 07 21 27_65eae0be](https://github.com/user-attachments/assets/462ea725-79d9-4567-9dd1-abb2fcf9912f)


### OUTPUT
![WhatsApp Image 2025-11-20 at 07 21 54_d1fd5bf2](https://github.com/user-attachments/assets/b07cf4c8-f0fe-4267-b087-1849b1d29f76)

   
### RESULT
The message signal, carrier signal, and phase-modulated (PM) signal will be displayed in separate plots. The modulated signal will show phase variations corresponding to the amplitude of the message signal.
