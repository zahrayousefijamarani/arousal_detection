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
## Arch
CNN for channel except SaO2:
![image](https://user-images.githubusercontent.com/45602698/141678020-ef31c54a-2bee-4ac1-9cd0-8a2b180c9256.png)
CNN for SaO2:
![image](https://user-images.githubusercontent.com/45602698/141678080-94deaa1b-b6f7-45b9-8ba1-3f7942db0c31.png)
### Convolution layers
![image](https://user-images.githubusercontent.com/45602698/141678134-c53e5852-f59c-4b7b-af57-9573f7fdabdf.png)
##### Example 
![image](https://user-images.githubusercontent.com/45602698/141678176-894eb8b9-0cb8-4c53-942f-03d7a7c5c4e0.png)
### Max-Pooling
1D max-pooling
Pool-size = 2
Stride = 1
### PReLU
As activation
### Drop-Out
Rate = 0.33
The Dropout layer randomly sets input units to 0 with a frequency of rate at each step during training time, which helps prevent overfitting. Inputs not set to 0 are scaled up by 1/(1 - rate) such that the sum over all inputs is unchanged.
### Flatten layer
To remove all of the dimensions except for one
### Fully Connected layer
There are 3 Dense layers that after each one there is a PReLU layers and Dropout layer.
All channels except SaO2 have [256,128,128] units and SaO2 has [512,256,64,64] units



