# Self Driving car using Kivy and TD3

[![Alt text](https://img.youtube.com/vi/SO3KbC9EGHw/0.jpg)](https://www.youtube.com/watch?v=SO3KbC9EGHw)

### GameMain.py:
This is the main py file. Here the kivy environment of Assignment 7 was modified to use the T3D from Assignment 10, to drive the car on the map.
The car is initialized in a random positions. 
Initially for 1000 time steps the car takes random action to fill the experience replay buffer. For the next 10000 time steps the TD3 is trained. The model is used after 10000 timesteps for maximum 500000 steps.

### The State of the car 
##### CNN features:
The the cut out of the sand/map corresponding to the position of the car is passed through a CNN model that is pretrained with MNIST dataset. The output features of the the MNIST layer would represent the position of the road. 
Alternatively I would want to change the design such that the image of the sand and the car are super imposed and pased through, entirely without cropping, to a Network that is trained to process bigger images. 

##### Other State parameters:
Along with the output features of the MNIST layer we add the orientation of the car, the velocity of the car to add more information of the state to TD3.
I suppose resizing the cropped car image to 28x28 does not show much information. 

### Action for the car:
The Action is the output of the TD3 model is one value which represent the angle to be taken by the car. The value of the action represents the quantity of the action. 
Further I would have wanted to add the speed as another action parameter. Currently the speed on the sand and the road and kept fixed, just as before.

### Results:
The Car moves properly while taking random actions. Once the TD3 model is used to predict the action the car just spins in one place.

## Future corrections and improvements:
