# Gravitational Wave Data Analysis Projects

This repository contains two small gravitational-wave data analysis projects using publicly available detector data from the Gravitational Wave Open Science Center (GWOSC).

The goal of these projects is to demonstrate core techniques used in gravitational-wave astronomy, including detector conditioning, matched filtering, template-bank searches, and time–frequency signal reconstruction.

Both analyses use real detector strain data from LIGO for the event GW150914, the first observation of gravitational waves from a binary black hole merger.


---

# Project 1  
# Simplified Compact Binary Search Pipeline

This notebook implements a simplified version of the search strategy used by the LIGO Scientific Collaboration (LSC) to identify compact binary mergers.

The analysis demonstrates how gravitational-wave signals can be detected by filtering detector data against a bank of theoretical waveform templates.

## Pipeline Overview

1. Download detector data  
   Strain data from the Hanford (H1) and Livingston (L1) detectors is downloaded from GWOSC.

2. Detector conditioning  
   The detector data is prepared for analysis by:
   - converting strain data to a PyCBC time series
   - estimating the detector noise power spectral density (PSD)

3. Template waveform generation  
   Theoretical compact-binary inspiral waveforms are generated for a small grid of component masses.

4. Matched filtering  
   The detector strain is filtered against each waveform template to compute a signal-to-noise ratio (SNR) time series.

5. Trigger identification  
   For each template:
   - the peak SNR is located
   - triggers are ranked by detection strength

6. Multi-detector consistency  
   The best triggers from H1 and L1 are compared to verify that their peak times are consistent within the light travel time between detectors.

## Example Results

The pipeline successfully recovers a strong SNR peak near the event time in both detectors.

The best-performing template corresponds to component masses close to the true system parameters of GW150914.

Recovered quantities include:

- matched-filter SNR time series
- ranked template triggers
- detector coincidence timing
- comparison of best-fit template parameters

This notebook demonstrates the fundamental principle behind gravitational-wave detection: matched filtering against theoretical waveform templates.

---

# Project 2  
# Time–Frequency Reconstruction of a Gravitational Wave Chirp


This notebook analyzes the same event using a time–frequency approach rather than matched filtering.

Instead of searching with templates, the goal is to visually reconstruct the gravitational-wave chirp directly from the detector data.

## Pipeline Overview

1. Download detector strain data

2. Condition the data
   - bandpass filtering
   - whitening

3. Construct a spectrogram
   A spectrogram is computed to visualize signal power as a function of time and frequency.

4. Extract the chirp ridge
   The brightest frequency at each time slice of the spectrogram is selected to approximate the signal track.

5. Track frequency evolution
   The extracted ridge demonstrates the rising-frequency inspiral signature expected from a compact binary merger.

## Results

The spectrogram reveals the characteristic chirp pattern of a compact binary inspiral: a rapidly increasing frequency as the system approaches merger.

An approximate ridge extracted from the spectrogram follows this rising frequency track.

While the ridge allows a qualitative estimate of the chirp evolution, precise parameter estimation requires matched filtering and large template banks.

This notebook therefore illustrates how time–frequency visualization complements template-based searches in gravitational-wave data analysis.

---


# Learning Goals

These notebooks demonstrate several core concepts in gravitational-wave data analysis:

- detector strain conditioning
- noise power spectral density estimation
- matched filtering
- template bank searches
- signal-to-noise ratio time series
- multi-detector coincidence
- time–frequency visualization of gravitational-wave signals

---

# Notes

These projects are educational demonstrations and do not reproduce the full search pipelines used by the LIGO–Virgo collaborations.

Nevertheless, these notebooks illustrate the fundamental methods used in gravitational-wave data analysis
