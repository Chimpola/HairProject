# LearningToWalk

This project develops a system that allows a generative adverserial neural network to generate new/unique data that will drive avatar walking behaviour in a virtual environment (VE). You will need to have a basic proficinecy in using a game engine, specifically Unity, and have some understanding of the use of skeletal movement data to drive avatar meshes. A basic understanding of deep learning, particularly convolutional nets and generative adversarial systems, would be helpful although not necessary as the code is provided.

The VE is built in Unity 5.6.xxx
The avatars were created using ManuelBasioniLabs v1.5 within Blender 2.78. The rest of the assets, clothes and shoes etc., were created by the experimenters. 

The Unity scene consists of two avatars: a driver and a copier. The driver avatar can either use live mocap data or pre-recorded data. The movement data output from the driver is deposited in an output file (.csv) which can be subsequently read and reproduced by the copier avatar. However, this would only produce simple copied behaviour in the 2nd avatar.

In order to teach the copier avatar to move with unique, realsitic yet machine generated behaviour the process can be interupted after the diver creates the output file but before the copier reads it. The data in the output file is fed into a generative adverserial network which learns to reproduce that form of movement. The further output from this system can then be fed back to the Unity scene to drive the copier avatar. With enough samples, it should be possible to teach the machine how to imitate an individual's style of movement, particularly if limiting to one category of movement such as a walk cycle. Alternatively, the walking style of a group of people could be imitated,creating a group style generatable on demand. Even more inclusively, a general realistic human walking style could be created.

This technique is not a simple averaging of movement data to produce, for example, a single movement cycle. Once the system has learned a movement, style and all, it will be able to produce new yet realistic versions of that movement, capturing the character of the movement. This could be used to add a further layer of realism in a video game, for example, beyond the simple repetition of 'canned' animation.

Although this system would not be a real-time solution it is a first step on the way to such.

_________________________________________________________________


Points to note:

1. we imported hundreds of walk cycles into the Unity project. The high number of cycles reflects the 'big data' origins of the machine learning techniques; the algorythms need many samples to learn the character of the movement type. 

2. for this initial project, the skeletons of the movement files need to be either identical to the standard driver avatar skeleton (given below) or at least be mapped to the Unity humanoid system (confusingly called an 'avatar' also).

3. for simplicity, we kept each movement file the same length, 2 seconds, at 30 frames per second. Unity can be capped to run at this speed and, provided the hardware is capable, should not drop below it so producing a constant speed of output. The csv file created is written to give one frame of skeleton movement per line. Therefore, every 60 lines represents one walk cycle.

4. ideally, each of the cycles should begin and end with the limbs in approximately the same position as each other for a better result, although the Unity Mechanim system can smooth between these as needed. In future, we may be able to tween the gaps automatically by adjusting the output file but this is not a current priority.

5. the neural network is adapted from one that was designed to create new hand written digits (http://yann.lecun.com/exdb/mnist/, ref....O'Reilly). In order to use the network without too much adaption, we turned the skeletal movement into a something approaching image data as follows:

	- the original data represented greyscale 28x28px images but 	  the neural network is flexible as long as the image is a 	  	  square(maybe rectangle possible?). We used ....x.... which 	  allows one frame of 
	  skeletal positioning per horizontal line as well as ....
 	  rows, allowing for a two second window, at 30fps, where 
	  the left foot is touching the ground. This should give a
 	  smoother final result (see point 4. above). There was some
 	  redudundancy in the 'images' but this was proportionally
 	  much less than the original MNIST dataset for instance.

	- a python script (theCutter.py) was used to prepare the
 	  data prior to feeding into the neural net. It 

	- greyscale values normalised in MNIST? Normalised here?






