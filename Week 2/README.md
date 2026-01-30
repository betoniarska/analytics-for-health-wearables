Analytics for health wearables exercise 2: Time domain heart rate and heart rate variability analysis

1. ECG Preprocessing & T-Wave Suppression
Before peak detection, the ECG signal needs to be preprocessed to enhance QRS complexes and suppress low-frequency components such as baseline wander and T-waves.

Processing steps: Pan-tompkins preprocessing pipeline

Bandpass filtering to isolate the QRS frequency band
Derivative filtering to emphasize steep slopes
Squaring and moving-window integration to locate peaks more accurately

2. Peak Detection via Local Maxima
R-peaks were detected using a local-maximum-based approach applied to the moving-window-integrated (MWI) ECG signal.
The MWI enhances QRS complexes while suppressing P- and T-waves, enabling robust peak detection using adaptive thresholds
on peak height, prominence, and a minimum inter-peak distance to enforce physiological plausibility. Detected peaks in the MWI
signal were then temporally mapped back to the band-pass filtered and original ECG signals by searching for the maximum amplitude
within a fixed ±150 ms window around each MWI peak.

4. Heart Rate Computation & Physiological Beat Rejection

Heart rate is computed from detected R-peaks using RR intervals:
Physiological constraints are applied to remove implausible beats:
Minimum heart rate (e.g., 40 bpm)
Maximum heart rate (e.g., 200 bpm)
Beats producing RR intervals outside these limits are rejected.

4. Heart Rate Variability (HRV) Analysis

HRV is estimated using Poincaré (Lorentz) plots, constructed from consecutive RR intervals:

SD1 – short-term (beat-to-beat) variability
SD2 – long-term variability
Clean ECG signals produce compact, elliptical Poincaré plots, while motion-corrupted signals exhibit broader, more scattered distributions, reflecting increased apparent HRV due to detection jitter and artifacts.

5. ECG–PPG Delay Estimation

The average time delay between electrical cardiac activation and peripheral pulse arrival is computed by pairing:

ECG R-peaks

The subsequent PPG foot (pulse onset)
PPG foot locations are detected using a slope-based (derivative) method appropriate for PPG morphology (Pan–Tompkins is not used for PPG).
The delay for each beat is computed as:
Physiologically implausible delays are rejected.
