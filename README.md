**Name:** Jeswin Shalom S  
**Roll Number:** 212223060106

# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To implement Pulse Code Modulation (PCM) using Python for a sinusoidal signal, including sampling, quantization, and encoding into binary form.

# SOFTWARE REQUIRED
1. Google colab (Python)
2. Numpy
3. Matplotlib

# ALGORITHMS
1. Generate a sinusoidal signal using a high-resolution time vector.
2. Sample the sine wave at uniform intervals based on a chosen sampling frequency.
3. Round each sampled value to the nearest level from a fixed number of quantization levels.
4. Encode each quantized value into a binary format.
5. Decode the binary data back into quantized values.
6. Use decoded quantized values to recreate a step-wise version of the original signal.
7. Plot the original, sampled, quantized, and reconstructed signals

# PROGRAM
```
import numpy as np
import matplotlib.pyplot as plt  # Missing import added

# Parameters
sampling_rate = 5000  # Samples per second
frequency = 50  # Frequency of the analog message signal
duration = 0.1  # Duration in seconds
quantization_levels = 16  # Number of quantization levels

# Time vector
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

# Message signal (sine wave)
message_signal = np.sin(2 * np.pi * frequency * t)

# Clock signal with increased frequency (200 Hz)
clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

# Quantization
quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
quantized_signal = np.round(message_signal / quantization_step) * quantization_step

# PCM encoding: normalize and convert to integers
pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step
pcm_signal = pcm_signal.astype(int)

# Plotting
plt.figure(figsize=(12, 10))

# 1. Message Signal
plt.subplot(4, 1, 1)
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')
plt.title("Message Signal (Analog)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# 2. Clock Signal
plt.subplot(4, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal (200 Hz)", color='green')
plt.title("Clock Signal (Increased Frequency)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# 3. PCM Modulated Signal (Quantized)
plt.subplot(4, 1, 3)
plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')
plt.title("PCM Modulated Signal (Quantized)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# 4. Simulated Demodulated Signal
plt.subplot(4, 1, 4)
plt.plot(t, quantized_signal, label="Demodulated Signal", color='purple', linestyle='--')
plt.title("Simulated Demodulated Signal")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()
```

# OUTPUT
 ![image](https://github.com/user-attachments/assets/d83e43ff-76e1-4d3f-9d4a-027e5df49534)

# RESULT / CONCLUSIONS
Thus the pulse code modulation converts an analog sine wave into a digital signal and the graph is obtained.
