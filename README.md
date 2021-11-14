# Arousal Detection
![image](https://user-images.githubusercontent.com/45602698/141677980-42a3a25a-abee-4c5f-bad8-be1d4c8c30c4.png)
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
![image](https://user-images.githubusercontent.com/45602698/141677888-272455ba-4bcd-4b72-a7b6-e14826455286.png)
## Batch-Size
The batch size is a number of samples processed before the model is updated
Batch-size is 32 Chunk
Batch-size/2 is positive windows(most labeled as 1)
Batch-size/2 is negative windows(most labeled as 0)
### Chunk
Chunk contains X_Prev, X, X_Next after pre-processing.
### How to choose Batch-size/2
Choose batch-size/2 of users randomly, choose on of the positive or negative windows from each users.
## Other Pre-Processings
![image](https://user-images.githubusercontent.com/45602698/141677937-4c5e9905-7571-4ef5-a152-b5de0b8ff8f9.png)

