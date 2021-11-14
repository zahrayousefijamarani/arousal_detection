# Arousal Detection
## Windowing
Window size is 30 seconds, 
Windows have NOT Overlap in training
### Windowing Process
- Move Window (15 seconds with overlap, 30 without overlap)
- Find the most labels as Y
- Save in file( x, x_prev(-1), x_next(-1))
## Input
The input of the Neural network is 1400 samples that is 28 seconds(Data downsampled to 50Hz)
Windows size is 30 seconds(1500 sample). 
### How to Get 1400 samples from 30 seconds
Cropping
If the length of a window is more than 1400 samples then choose 1400 consecutive samples from it randomly.

