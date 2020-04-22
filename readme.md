# Auto cropping for images

CHIU, Ka Ho kchiu40@gatech.edu

## Description

A simple function for auto cropping images, with their possible descriptions if needed, from a pdf file.

The reason choosing pdf file is that are the pictures, no matter text images or those with pictures, are in pdf format.

However this function only provides the part to read from png file, as there are several apis available for doing the step from pdf to png already.

The libraries used in this function are cv2 and random.



## Method

* Gaussian Blur 
* Canny Edge Detection 
* Dilation (possibly better Erosion first then Dilation to get rid of full text, but not implemented as it is not needed for most pdf files here) 
* Contours 
* Save those contours close to rectangle
* Crop



## Possible product

* Images with contours
* Images with rectangle regions labelled
* <u>Cropped Images</u>



## Inputs

Most of them are default, except `input_path`.
`input_path` is the path from current folder to the png file, on the otherhand `output_path` is given `"segment/{}.png"` as default, but it needs a created segment folder sometimes.



## Example

For example the image with input path `"pic/21-43-11/56b0183fdbff00aed3f9d0e369184128-1.png"`

(21-43-11 actually refers to the way for how to find this pdf in the database)

![56b0183fdbff00aed3f9d0e369184128-1](https://user-images.githubusercontent.com/32212138/79998407-ab257980-8488-11ea-809a-55277ec87494.png)


If we do

```python
autoCrop('pic/21-43-11/56b0183fdbff00aed3f9d0e369184128-1.png')
```

We get the following pictures

![0](https://user-images.githubusercontent.com/32212138/79998664-f9d31380-8488-11ea-9304-3c6fb80cc9cc.jpg)

![1](https://user-images.githubusercontent.com/32212138/79998665-fa6baa00-8488-11ea-86ce-b0d43a0dd388.jpg)

![2](https://user-images.githubusercontent.com/32212138/79998666-fa6baa00-8488-11ea-8f8e-6673985871cd.jpg)

![3](https://user-images.githubusercontent.com/32212138/79998667-fa6baa00-8488-11ea-872c-76709de8e2f1.jpg)

![5](https://user-images.githubusercontent.com/32212138/79998668-fa6baa00-8488-11ea-92fd-3454feb8c83b.jpg)

![6](https://user-images.githubusercontent.com/32212138/79998669-fa6baa00-8488-11ea-9a72-74c3d07dc4b2.jpg)

![7](https://user-images.githubusercontent.com/32212138/79998670-fb044080-8488-11ea-85bd-011f374f1127.jpg)

![8](https://user-images.githubusercontent.com/32212138/79998671-fb044080-8488-11ea-9bcc-97a57b9d5a14.jpg)

![19](https://user-images.githubusercontent.com/32212138/79998672-fb044080-8488-11ea-92cb-cf8ff3634d3c.jpg)

![20](https://user-images.githubusercontent.com/32212138/79998673-fb044080-8488-11ea-8483-06a758dbe05b.jpg)



Which is very nice.



## Improvement

* The simple api is on its way.

* For the parameters we still need some manual tunning, I tried to use AdaBoost here but the result is not that well. The problem here is that it's not quite clear how to determine whether a crop is good or not, as we involve not only images but also its text descriptions.

* Sometimes the result also include blocks of text, i.e. not images, so we need some further things to clean this up. I personally used cnn and it works well, but I do recommend Humas Lin's method as it is absolutely more powerfully than mine.
