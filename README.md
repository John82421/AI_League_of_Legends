# Level 1 - Shoot "Auto Q skills" on the enemy on Image Recognition

Based on the image recognition, the model that I create with 1,500 pictures is able to detect the enemy on League of Legends and makes ezreal shot "Q" to the enemy on the coordinate of x and y axis. 

# Explaination (Classification and Object Detection)

# 1. Images

I respectively save 500 images of Tower, Minion, and Ezreal on League of Legends (Total 3 classes)
- Used parser or tf.run.flags to insert width, height, and filename
- Used cv2 to take each 500 pictures
- Saved those pictures with np.save(The size of .npy is 233.4 mb)

![1](./git/1.png)

# 2. Model 

:Used AWS to use GPU that has p2.x2large to operate model. I have used 3540 epochs on GPU based on Object Detection.

![4](./git/4.png)

# 3. Tensorboard(the function of early stopping is in the file, model.py) 

![5](./git/5.png)

# 4. Result - Shooting "Auto Q skills" on the enemy

[![Watch the video](./git/11.png)](https://www.youtube.com/watch?v=qrJkvGzGvkE&feature=youtu.be)



# Installation

- You can install some packages, tensorflow, argparse, pillow, and numpy

`pip install -r requirement.txt`

# How to Use Classification and Object Detection

1. To create .npy and 500 pictures, use tf_save_image.py

`python tf_save_image.py --filename LOL_data.npy`

2. If you run it, the file LOL_data.npy on the folder of data is created and 1,500 images are saved on the image folder of images.

3. To seperate LOL_data.npy into two groups, train_data and image_data, you might as well use tf_load_image.py

`python tf_load_image.py --filename LOL_data.npy`

4. To create a model, you might use model.py that has CNN mode(I used early-stopping with patience = 5 and made the model stopped actumatically, also made use of Dataset API)

`python model.py`
`python prediction.py`

5. To make the box on the picture, ImageGrab on Pillow and Tensorflow Object Detection API might be used to detect ezreal, tower, and minion

6. To detect and controll ezreal automatically, you might use contoller.py

`python controller.py`


[![Watch the video](https://www.youtube.com/embed/6Az2cNU7gUw)](https://www.youtube.com/watch?v=qrJkvGzGvkE&feature=youtu.be)


# LEVEL 2 - Predict the enemies' movement 

If we can detect the object, Ezreal, Tower, and Enemy, we might detect the motion of object. For example, when we use Blitz or Thresh, we are able to grab the enemy based on the prediction of movement.

# How to predict the enemies' movement

I try to use 300,000 images to recognize the motion of Ezreal. Ezreal moves anywhere 360 degree but that is depending on the shape of map. Map A, attached, has two ways to avoid the skills upside and downside. Otherwise, Map B, below has also two ways to shy away from the grabs rightside and leftside. I make use of this method on the Classification.

![12](./git/12.png) 

# Map A

![13](./git/13.png){:height="30%" width="30%"} 

# Map B

![14](./git/14.png){:height="30%" width="30%"}



