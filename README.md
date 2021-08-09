This is my first ML project. My goal for this project is to use VAE and generate random pictures of Cristiano Ronaldo.

Results:

![](https://github.com/mifanbing/poseVAE/blob/main/result_15.png)   ![](https://github.com/mifanbing/poseVAE/blob/main/result_17.png)

The face is blurry, body and pose are more clear, and the jerseys are recognizable (Juventus and Real Madrid).

Data Preparation:
I am doing this project on my own, so data preparation is hard. My original plan was to collect pictures of Ronaldo's full body, get all the joints and generate pictures based on the input pose. Data collection turns out to be too hard, so I took a step back and tried generate random pictures of Ronaldo first.

I used Imageye to download images from Chrome, converted all pictures to RGBA, and used MediaPipe to remove the background (mediapipe.ipynb)
I think that background, usually with a few other people, will make training hard, so I remove the background to improve data quality.

Raw Image          |  Image with background removed
:-------------------------:|:-------------------------:
![](https://github.com/mifanbing/poseVAE/blob/main/rawImage.jpg) | ![](https://github.com/mifanbing/poseVAE/blob/main/imageRemoveBackground.jpg)

I have around 3k images. Maybe I need more to get better results.

Model:
I used the standard VAE model - a decoder followed by an encoder. It's hard to guess what parameters are good to start with, and I failed hard. I found a VAE project from (https://towardsdatascience.com/generating-new-faces-with-variational-autoencoders-d13cfcb5f0a8) and referenced the model structure and parameters.

Training:
I defined the total loss as reconstruction loss + KL loss, the factor can be tuned and I have tried a few, this one seems to work best for me now. 
I found that using a PolynomialDecay optimizer works better. 
Dropout layer seems to be not needed.

Generate my own images:
Wrote some code (https://github.com/mifanbing/poseVAE/blob/main/generate.ipynb)
Note that I was using tf.keras.models.load_model() but later found that it doesn't work for me. The weights are not correct - it doesn't generate same image as the encoder in (https://github.com/mifanbing/poseVAE/blob/main/poseVAE.ipynb)

For next step, I want to do something like conditional GAN and generate images based on input pose. Will keep tuning this model at the same time.

I got a lot of help from my friends, thank you. Won't reference you guys yet since the results are not great yet lol.
