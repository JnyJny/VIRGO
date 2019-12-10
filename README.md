# VIRGO: An open-source spectrometer for radio astronomy
![alt text](https://i.imgur.com/PR2wpse.png "VIRGO Spectrometer")

## About VIRGO
**VIRGO** is an easy-to-use **open-source** spectrometer and radiometer based on [Python](https://www.python.org) and [GNU Radio Companion](https://wiki.gnuradio.org/index.php/GNURadioCompanion) (GRC) that is conveniently applicable to any radio telescope working with a GRC-supported software-defined radio (SDR). VIRGO 

A list of GRC-supported SDRs can be found [here](https://wiki.gnuradio.org/index.php/Hardware).

## GRC Data Acquisition Flowgraph
**VIRGO** is a [**polyphase filterbank** spectrometer](https://arxiv.org/abs/1607.03579). The raw I/Q samples are processed in real time using GNU Radio, with the amount of data stored to file being drastically reduced for further analysis. The following flowgraph handles the acquisition and early-stage processing of the data:

![alt text](https://i.imgur.com/2Xp8qnZ.png "Data Acquisition Flowgraph")

## Spectral leakage: a comparison between ACS, FTF and PFB spectrometers
One of the advantages of polyphase filterbanks is **reduced spectral leakage**. The following figure compares the spectral leakage produced by an autocorrelation spectrometer (ACS), a Fourier transform filterbank spectrometer (FTF) and a polyphase filterbank spectrometer (PFB) with a Hann FFT window:
![alt text](https://i.imgur.com/e5TwE3w.png "Spectrometer comparison regarding spectral leakage")
Source: [Danny C. Price (2018)](https://arxiv.org/abs/1607.03579)

## A graphical representation of a polyphase filterbank
![alt text](https://i.imgur.com/HUFTmTh.png)
Source: [Danny C. Price (2018)](https://arxiv.org/abs/1607.03579)

## ata analysis
Once a submitted observation is finished and the data has been acquired and stored to `observation.dat`, the FFT data (interpreted as a [numpy array](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html) in `plot.py` and `plot_hi.py`) constitutes the **dynamic spectrum (waterfall)**, from which the **averaged spectrum** and **time series (power vs time)** of the observation can be derived.

We can mathematically interpret the dynamic spectrum as a *2*-dimensional matrix with ***m*** rows and ***2<sup>n</sup>*** columns, where *m* ∈ ℕ\* is the total number of FFT samples (integrations) and *2<sup>n</sup>*, *n* ∈ ℕ is the number of frequency channels (FFT size).

In `plot.py` and `plot_hi.py`, this matrix is defined  are averaged along the vertical and horizontal axis



**m⋅t<sub>int</sub>**