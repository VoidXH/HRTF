# Cavern virtualizer measurements
This repo contains the source impulse responses for Cavern's headphone
virtualizer.

## Cavern pipeline
![Cavern pipeline](Cavern%20pipeline.png)

Since the impulses are cut to 64 samples, Cavern is optimized to this with
calculating convolutions by definition, which means it's not a HRTF, but a HRIR.

## How it's made
These impulse responses are home-made with a cheap setup. They offer mediocre
spatial cues, but little artifacts with a more flat frequency response than most
free HRTF databases. The results are based on a single subject, with the
following setup in a small room (hence the 64 sample length for the aligned
impulses):
* A pillar of Klipsch R-15M speakers
* Genius SW-G 2.1 3000 amplifier
* JBL E15 microphone in the pinna directed to the ear canal
* Cavern 1.2 QuickEQ set to 65536 samples, using the room simulation export
feature, which is available in Cavern 1.3

The usable frequency range of this setup is 120-12500 Hz. Any sound below 120 Hz
shouldn't be spatialized, even with IRs that support it.
