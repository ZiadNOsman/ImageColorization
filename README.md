# ImageColorization
Turned Images to RGB matrix then converted them to Lab space. Used a convolutional neural network to predict the values of the pixels and then re- rendered the greyscale images as colored images

## approach
In LAB space, similar to RGB, we have 3 components: L, a* and b*. However, unlike in RGB, the L component in LAB space represents lightness, which is the same for an image whether the image was colored or in greyscale. What that means is, when the user inputs a greyscale image, we already have the component L, which means we only have the two remaining values a* and b*. Note that if we were representing our images in lgb, we would have to predict three values Red, Blue and green, making LAB space the obvious choice.  
With our method in place, we learned how to convert images into matrix form, and learned how to convert from grey-scale to L, and, eventually, learned how to convert from LAB space to RGB in order to plot the output.
![image](https://user-images.githubusercontent.com/67204880/148967972-ce8536bc-cacc-40f1-91bc-e7f523f64eab.png)
