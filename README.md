# PSK
# Aim
Write a simple Python program for the modulation and demodulation of PSK and QPSK.
# Tools required
# Program
# PSK
```
fs = 1000          
Tb = 1            
fc = 5             
data = [1,0,1,1,0,1]

t = np.arange(0, Tb, 1/fs)
message = np.repeat(data, len(t))
time = np.arange(len(message)) / fs
carrier = np.sin(2*np.pi*fc*time)
polar_data = 2*message - 1
psk = polar_data * carrier

demod = psk * carrier
reconstructed = (demod > 0).astype(int)


plt.figure(figsize=(12,8))

plt.subplot(4,1,1)
plt.plot(time, message)
plt.title("Message Signal")
plt.ylim(-0.5,1.5)
plt.grid()

plt.subplot(4,1,2)
plt.plot(time, carrier)
plt.title("Carrier Signal")
plt.grid()

plt.subplot(4,1,3)
plt.plot(time, psk)
plt.title("PSK Modulated Signal")
plt.grid()

plt.subplot(4,1,4)
plt.plot(time, reconstructed)
plt.title("Demodulated Signal")
plt.ylim(-0.5,1.5)
plt.grid()

plt.tight_layout()
plt.show()

```
# QPSK
```
import numpy as np
import matplotlib.pyplot as plt

fs, Tb, fc = 1000, 1, 5
data = [1,0, 0,1, 1,1, 0,0]  

t = np.arange(0, Tb, 1/fs)


I = np.repeat(data[0::2], len(t))
Q = np.repeat(data[1::2], len(t))
time = np.arange(len(I))/fs

c1 = np.cos(2*np.pi*fc*time)
c2 = np.sin(2*np.pi*fc*time)
qpsk = (2*I-1)*c1 + (2*Q-1)*c2
I_rec = (qpsk*c1 > 0).astype(int)
Q_rec = (qpsk*c2 > 0).astype(int)

reconstructed = np.ravel(np.column_stack((I_rec, Q_rec)))
plt.figure(figsize=(12,8))

plt.subplot(4,1,1)
plt.plot(time, I)
plt.title("Message Signal")
plt.ylim(-0.5,1.5); plt.grid()

plt.subplot(4,1,2)
plt.plot(time, c1)
plt.title("Carrier Signal")
plt.grid()

plt.subplot(4,1,3)
plt.plot(time, qpsk)
plt.title("QPSK Modulated Signal")
plt.grid()

plt.subplot(4,1,4)
plt.plot(time, reconstructed[:len(time)])
plt.title("Demodulated Signal")
plt.ylim(-0.5,1.5); plt.grid()

plt.tight_layout()
plt.show()

```
# Output Waveform
# PSK
<img width="1189" height="790" alt="image" src="https://github.com/user-attachments/assets/11850989-fa03-42c4-a792-c89d40f35b5d" />

# QPSK

<img width="1190" height="790" alt="image" src="https://github.com/user-attachments/assets/9e444de2-52bf-46d4-adc1-e43b70d75954" />


# Results
```
Attach the output waveform
```
# Hardware experiment output waveform.
