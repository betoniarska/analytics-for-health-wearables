This repository contains a step-by-step biomedical signal processing pipeline applied to simultaneously recorded ECG and PPG signals (clean and motion-corrupted).
The goal of the exercise is to inspect, preprocess, analyze, and filter the signals while preserving physiological information.

Preprocessing pipeline:

1. Visual inspection (time domain)

ECG and PPG signals were plotted for both clean and motion datasets.
Visual inspection was used to assess:
  Signal quality
  Motion artifacts
  Differences between clean and motion recordings

2. Resampling to a common sampling frequency

Original sampling rates:
  ECG: 128 Hz
  PPG: 100 Hz
All signals were resampled to a common sampling frequency of 200 Hz to ensure:
  Equidistant samples
  Equal signal length
  Direct comparability in time and frequency domains

3. Frequency-domain analysis (FFT)

Expected and observed frequency content:

ECG
  Dominant peak at ~1–1.5 Hz (heart rate)
  Harmonics extending up to ~40 Hz
  Clean ECG shows clear harmonic structure
  Motion ECG retains the dominant heart-rate peak but loses harmonic coherence

PPG
  Dominant cardiac component at ~1–1.5 Hz
  Most signal energy below ~5 Hz
  Motion PPG is dominated by strong DC and very-low-frequency components caused by motion-induced baseline drift

4. Filtering (Butterworth & moving average)

Applied signal passband according to prior task (fft)
  ECG	0.5 – 40 Hz
  PPG	0.5 – 7 Hz

  Clean ECG showed minimal visual change after filtering, indicating good signal quality.
  Motion PPG showed substantial reduction of low-frequency baseline drift.
  Motion ECG artifacts largely remained, as they overlap the ECG frequency band.




