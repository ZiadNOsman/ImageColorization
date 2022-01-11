# ImageColorization
Turned Images to RGB matrix then converted them to Lab space. Used a convolutional neural network to predict the values of the pixels and then re- rendered the greyscale images as colored images

## approach
In LAB space, similar to RGB, we have 3 components: L, a* and b*. However, unlike in RGB, the L component in LAB space represents lightness, which is the same for an image whether the image was colored or in greyscale. What that means is, when the user inputs a greyscale image, we already have the component L, which means we only have the two remaining values a* and b*. Note that if we were representing our images in lgb, we would have to predict three values Red, Blue and green, making LAB space the obvious choice.  
With our method in place, we learned how to convert images into matrix form, and learned how to convert from grey-scale to L, and, eventually, learned how to convert from LAB space to RGB in order to plot the output.
![image](https://user-images.githubusercontent.com/67204880/148968065-dbf3e6b7-3b5a-444e-b54e-0c796354ba89.png)

## dataset
We started off with 21,000 colored images. we converted the images to matrix form. the matrix form images were in RGB, and so we used a function to turn them from RGB to LAB space. Also, we split the matrix form images into two sub-matrices, one containing the L values, and the other containing the a* and b* values. Finally, we fed our CNN with L values and let it output predicted a* and b* values (which the CNN compared to the real a* and b* values)
## model 
We used CNN for our model.  
To stay on the simple side, and to prevent our computers from dying, we decided to use 12 convolutional layers. In addition, we used 3 up-sampling layers to reduce the pixelation effect and so that the model can zoom more on small regions. And so, our Up-sampling layers improve accuracy.  
Its important to note that, since we care about each pixel separately, we opted out of using pooling layers as we thought it would negatively affect our results (since it only considers limited info out of a set of pixels).  
![image](https://user-images.githubusercontent.com/67204880/148968587-0eed4642-e42a-40bb-a517-7e9207efaa06.png)

## LAB to RGB
After training our model, we input a black and white image. This image gets converted into a LAB space matrix, where the L is put into the CNN that predicts a* and b*. with our L, a* and b* values ready, we create an array to represent the predicted colored image, turn the array from LAB space to RGB and finally plot the predicted colored image.  
![image](https://user-images.githubusercontent.com/67204880/148968798-c056d94e-5ea6-4244-8d9b-1b6698f5ce69.png)

## results
We fed our CNN 21,000 images in LAB matrix form, specifically the L value. the CNN outputs predicted a* and b* values, upon which the CNN compares to the real values, after which it uses gradient descent to fix the weights accordingly. We ran the model for 50 epochs for a total of 8 hours of training time (using GPU). 

![image](https://user-images.githubusercontent.com/67204880/148968991-813a9efa-415d-4bf5-aadf-979670219889.png)
![image](https://user-images.githubusercontent.com/67204880/148969009-6fa49a69-0a8a-4de2-89f5-5705c4a7e686.png)

## problems we faced
(most obviously, this was our first model we made at it should have served as only a prototype. The model is the first point of failure, but the below reasons also contributed to the aformentioned results)  
We found that 21,000 images was not enough to train our model to predict accurate numbers. We also found our hardware to be a limiting factor in how much we could train our model, as we zigzagged around OOM (out of memory) errors every step along the way.  
How we went about preventing those is we split our data into subsets and trained our model on those subsets separately. The results of our trained model showed promise, we were seeing good blue predictions and okay green predictions. We are confident that with a bigger dataset and, more importantly, a stronger hardware (enabling a much higher number of epochs of around 1000), we would have been able to train a really solid model. 


