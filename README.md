This is my first ML project. My goal for this project is to use VAE and generate random pictures of Cristiano Ronaldo.

Results:

![](https://github.com/mifanbing/poseVAE/blob/main/result_15.png) |  ![](https://github.com/mifanbing/poseVAE/blob/main/result_17.png)

The face is blurry, body and pose are more clear, and the jerseys are recognizable (Juventus and Real Madrid).

Data Preparation:
I am doing this project on my own, so data preparation is hard. My original plan was to collect pictures of Ronaldo's full body, get all the joints and generate pictures based on the input pose. Data collection turns out to be too hard, so I took a step back and tried generate random pictures of Ronaldo first.

I used Imageye to download images from Chrome, converted all pictures to RGBA, and used MediaPipe to remove background (mediapipe.ipynb)

