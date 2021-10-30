# Cavern virtualizer measurements
This repo contains the source impulse responses for Cavern's headphone
virtualizer and the simulated ear canal data for its distance simulation.

## Cavern pipeline
![Cavern pipeline](Cavern%20pipeline.png)

Since the impulses are cut to 64 samples, Cavern is optimized to this with
calculating convolutions by definition, which means it's not a HRTF, but a HRIR.
All IRs are aligned, which means further delays are required for the distant
ear's filter set. Cavern's formula is `(90 - |angle from ear - 90|) / 2.7` in
samples for 48 kHz sampling rate.

## File names
All files use counter clockwise azimuth angles. Top points are elevated 45
degrees from the listener. Ear canal simulation file names contain the angle
difference from the ear canal's outward direction and the object's distance from
the ear (e.g. D100) in centimeters.

## How it's made
These impulse responses are home-made with a cheap setup. They offer mediocre
spatial cues, but have the advantage of not requiring inverse filters to work
with headphones, not just earphones. The results are based on a single subject,
with the following setup in a small room (hence the 64 sample length for the
aligned impulses):
* A pillar of Klipsch R-15M speakers
* Genius SW-G 2.1 3000 amplifier
* JBL E15 microphone in the pinna directed to the ear canal
* Cavern 1.2 QuickEQ set to 65536 samples, using the room simulation export
feature, which is available in Cavern 1.3

The usable frequency range of this setup is 120-12500 Hz. Any sound below 120 Hz
shouldn't be spatialized, even with IRs that support it. Flattened filters
eliminate these issues, thus the need for any pre-processing, with their 0-24
kHz usable frequency range.

## How to use the examples
The example names are their use case. However, to virtualize actual 5.1, remove
the matrix splitting part from the decoder. Most stereo-only devices (like
notebook sound cards, stereo DACs) don't have a way of acquiring multichannel
audio on the OS level, this is sadly the best you can use.