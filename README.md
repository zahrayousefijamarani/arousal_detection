# Arousal Detection
## Windowing
Window size is 30 seconds, 
Windows have NOT Overlap in training
### Windowing Process
- Move Window (15 seconds with overlap, 30 without overlap)
- Find the most labels as Y
- Save in file( x, x_prev(-1), x_next(-1))
