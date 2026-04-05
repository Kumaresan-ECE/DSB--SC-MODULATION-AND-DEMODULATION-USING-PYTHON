# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

PROGRAM :
~~~
import numpy as np
import matplotlib.pyplot as plt

Am = 6.1
fm = 486
Ac = 12.2
fc = 4860
fs = 48600

t = np.arange(0, 2/fm, 1/fs)

m = Am * np.cos(2 * 3.14 * fm * t)

plt.subplot(3,1,1)
plt.plot(t, m)
plt.title("Message Signal")

c = Ac * np.cos(2 * 3.14 * fc * t)

plt.subplot(3,1,2)
plt.plot(t, c)
plt.title("Carrier Signal")

# DSB-SC Signal (carrier suppressed)
s = m * np.cos(2 * 3.14 * fc * t)

plt.subplot(3,1,3)
plt.plot(t, s)
plt.title("DSB-SC Signal")

plt.tight_layout()
plt.show()
~~~

   TABULATION :

   <img width="709" height="1280" alt="image" src="https://github.com/user-attachments/assets/df0f2e89-e469-423d-ac04-97f6aa504258" />


   OUTPUT :

   <img width="915" height="686" alt="image" src="https://github.com/user-attachments/assets/f794a137-2a3d-42ec-93af-800b0dc3d59a" />


   RESULT :

   <img width="703" height="1280" alt="image" src="https://github.com/user-attachments/assets/3c1dc0d2-1dfc-4330-9844-250b7dad6a61" />

