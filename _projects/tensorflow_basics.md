---
layout: page
title:  "Understanding Tensorflow Basics"
date:   2018-01-01 08:43:59
permalink: /tensorflow/
categories: ml
desc: "Understanding foundations of tensorflow and Image recognition"

---

**Technologies**: python3, tensorflow,tensorboard,machine learning, Deep Learning, KNN 

**Repo Link**: [link](https://github.com/Gaurav-Pande/MLCC/tree/master/tensorflow_basics)

**Note**: This is one of the resources/page for one to understand the basics of tensorflow. I found it pretty usefull to build and learn
tensorflow basics before starting the google machine learning crash coarse. If you are comfortable and know all the basics, than
this page is not for you.
You can directly run this project using google collab: [link](https://colab.research.google.com/drive/1plzYDCXRmW47nVRwZrlTcjap4-eY0APc)
Or you can just swipe through to grasp the summary.

## Basics

### Supervised ML algorithms:

* Suppose we have input variable x and output variable y

* Supervised machine learning algorithm task is to find a mapping function such that we can predict the 
   value of y with input x, that is : y = f(x). finding mapping function f is called supervised learning
   
* Approximate the learning function f, such that new values of x can be predict the value of y.
 
* we use existing training dataset to correct the mapping function approximation. 
 
 
### Unsupervised ML algorithms:
 
* Here we have input variable x but no output variable y.
 
* The goal of the algo is the find the model or pattern within the data to learn more about data and make prediction 
 
*  there is no supervision here, algorithms have to work on their own to make predictions.
 
 
### Deep Learning:
 
* **Traditional** ml based systems will rely on experts to decide what features to pay attention to. For example you will see in the linear regression problem, we have feed random value of A and b in equation: y = Ax + b, and get the best/optimized value of A,b so that the line is closest to all the datapoints
 
* **Representation** based ml system figure out by themselves what features to pay attention to.
 In the linear regression scenario the Representation system will able to pickup from a random value and optimized by itself to get the optimized value of A, b. 
 
 
* **Deep Learning** systems are one type of representation systems
 
### Deep Learning and Neural Networks:
 
* **Deep learning** : Algorithms which learns what feature matters
 
* **Neural networks**:  Neural Networks are the most common class of deep learning algorithms
 
* **Neurons**: Simple building blocks that actually learn by themselves
 
* **TensorFlow**: TensorFLow is an open source software library for numerical computations using Data
 flow graphs.
 
 
```
 import tensorflow as tf
 
```
 
 
#### Points to remember

* In tesorflow every problem in the world can be described in terms of a directly acyclic graph
* First we build a graph in tensorflow, so that the tensorflow have the knowledge of the whole graph and an understanding which parts of the graph are independent and can be run parallely in a distributed scenario(In different GPUs and CPUs)
* Each node in the graph is called compute node and the edges connecting the nodes are known as tensors.
* Output of one tensor is feeded to the input of the next node.

![Image](https://github.com/Gaurav-Pande/MLCC/blob/master/tensorflow_basics/assets/1.png)

* Than we initiate a session to execute the graph.
* And than finally we can run each nodes in the graph and can see their output.
* remember untill the session is not initialized, the graph will not executed.


#### Define constants or compute nodes first

```
  # These are the inputs that will be feeded to compute nodes
  a = tf.constant(6.5, name = 'constant_a')
  b = tf.constant(3.4, name = 'constant_b')
  c = tf.constant(3.0, name = 'constant_c')
  d = tf.constant(100.2, name = 'constant_d')

  # Now lets define some compute nodes
  square = tf.square(a, name = 'square_of_a')
  power = tf.pow(b,c, name = 'power_of_b_to_c')
  sqrt = tf.sqrt(d, name = 'square_root_of_d')

  #Now lets define the final node.
  final_node = tf.add_n([square,power,sqrt], name = 'final_node')

```
 
 
#### Now we initialize the session

```
  sess = tf.Session()

```
 
#### Now we can execute the nodes in the graph

```
  print ("Square of a is:",sess.run(square))
  print ("b to the power c is :",sess.run(power))
  print ("square root of d is:",sess.run(sqrt))
  print ("final result of all the nodes computation is:", sess.run(final_node))

```

#### Now write the summary to read the graph by tensorboard.

```
  writer = tf.summary.FileWriter('/tmp/m2_example',sess.graph)
  writer.close
  sess.close()

```

#### Tensor: What it is?

* A tensor is the basic unit in the tensorflow, all the input that we feed into the graph are called tensors.
* A tensor is of primitive type shaped into an array of any dimensions.

##### Properties of a tensor:
  * Rank: the number of dimensions in a tensor. Scaler(like 2,"a") have 0D tensor, [1,2,3] is 1-D tensor(basically number of square breacket pairs is the dimensionality of  a tensor)
  * Shape: It the number of elements in a tensor.e.g: [1,2]--> shape is [2]. [[1,2],[3,4]]--> shape si [2,2]
  * Datatype: the data type of the tensor

## Tensor Math

```
  # import tensorflow
  import tensorflow as tf
  # Define tensors
  x = tf.constant([100,200,300], name = 'tensor_x')
  y = tf.constant([1,2,3],name = 'tensor_y')
  # Define computation nodes
  sum_x = tf.reduce_sum(x,name='sum_x')
  prod_y = tf.reduce_prod(y,name = 'prod_y')
  final_div =  tf.div(sum_x,prod_y, name='final_div')

  # we can define the tensors on the fly as well
  final_mean = tf.reduce_mean([sum_x,prod_y],name='final_mean')
  # inititalize session
  sess = tf.Session()
  # execute the graph
  print ("x",sess.run(sum_x))
  print ('final_mean',sess.run(final_mean))

```

## Numpy and Tensor

* python accepts tensors and numpy arrays exactly the same. in fact tf.int32 == np.int32

```
  import numpy as np
  zeroD = np.array(30, dtype=np.int32)
  sess = tf.Session()
  sess.run(tf.rank(zeroD))
  sess.run(tf.shape(zeroD))
  
```

## Linear Regression

### Points to Remember

* Linear Regression is the classic example of supervised learning.
* Linear Regression can be represented by y = Ax + b
* In Ml it is more about finding the best fit line, ie the line which is closest to all the points on the dataset.
* Minimizing least square error is the way to find the best fit line. In this method you drop verticle lines from all 
the points to the line or equation you are inspecting, and the best fit line is that line which has least sum of squares 
of length of those vertical lines.

### Linear Regression Algorithm 

* equation of line: Y = Ax + B
* we start by estimating some value of A and B.
* Find the errors for the regression line with those values of A and B.
* feed error back to get the new value of the A and B.

### Placeholders

* It holds the value of the tensors, whose value will be available only at runtime.

```
  import tensorflow as tf
  # Defining a placeholder
  x = tf.placeholder(tf.int32, shape = [3], name = 'x')
  y = tf.placeholder(tf.int32, shape = [3], name = 'y')
  # Define Nodes
  sum_x = tf.reduce_sum(x, name='sum_x')
  prod_y = tf.reduce_prod(y, name='prod_y')
  final_div = tf.div(sum_x,prod_y, name='final_div')
  final_mean = tf.reduce_mean([sum_x,prod_y],name='final_mean')
  #Initiate a session
  sess = tf.Session()
  # Now compute the nodes
  # Notice now how we are feeding the input via feed dictionary method in placeholder
  print("sum of values of x", sess.run(sum_x, feed_dict = {x : [100,2,3]}))
  print("prod of values of y", sess.run(prod_y, feed_dict = {y: [1,2,3]}))
  print("final dic result:", sess.run(final_mean, feed_dict = {x:[2,3,4], y:[5,6,7]}))
  sess.close()
  
```

### fetches and feed dictionary

* we feed the values of the placeholder using feed_dict inplace parameter

```
  import tensorflow as tf

  # y = Wx + b

  W = tf.constant([100,200],name='constant_W')

  # define a place holder for x and b, note that placeholder can store tensors of
  # any shape

  x = tf.placeholder(tf.int32, name='x')
  b = tf.placeholder(tf.int32, name='b')

  Wx = tf.multiply(W,x, name='Wx')

  y = tf.add(Wx, b, name='y')

  # rather than initializing session and closing everytime, we will use the loop
  #
  with tf.Session() as sess:
    print ("Results are as:", sess.run(fetches=y, feed_dict = {Wx : [1,2], b : [1,2]}))

```

### Variables

* we know that in linear regression we start of by some value so A and b and than we tweak these values using feedback value, that means the value stored in A and b will keep on changing when we will run the algorithm, that is where variable are usefull.

#### In summary:
  * constants: immutable values whose value doesnt change.
  * placeholder: assigned once during runtime  and do not change after.
  * variable: constantly recomputed as the graph is recomputed.
  
```
  import tensorflow as tf

  # y = Wx + b

  W = tf.Variable([1.0, 2.0], tf.float32, name='var_W')

  # define a place holder for x and b, note that placeholder can store tensors of
  # any shape

  x = tf.placeholder(tf.float32, name='x')
  b = tf.Variable([1.0,2.0], tf.float32, name='b')

  y = W*x + b

  ## remember to initialize the variable, also note that is also a computation node
  init = tf.global_variables_initializer()

  # rather than initializing session and closing everytime, we will use the loop
  with tf.Session() as sess:
    sess.run(init)
    print ("Results are as:", sess.run(fetches=y, feed_dict = {x: [5.0, 6.0]}))



  s = W*x

  # Here i am only initializing the variables i need 
  init = tf.variables_initializer([W])

  with tf.Session() as sess:
    sess.run(init)
    print ("Results are as:", sess.run(fetches=s, feed_dict = {x: [5.0, 6.0]}))

```

### Default and Explicitly Specified Graph

* In all the programs that we have written above we are using the implicit default graph
* We can instantiate our own graph and perform all actions there as well.

```
  import tensorflow as tf

  g1 = tf.Graph()

  with g1.as_default():
    with tf.Session() as sess:
      # y = Ax + b
      A = tf.constant([5, 7], tf.int32, name='A')

      x = tf.placeholder(tf.int32, name='x')
      b = tf.constant([3, 4], tf.int32, name='b')

      y = A * x + b

      print (sess.run(y, feed_dict={x: [10, 100]}))

      assert y.graph is g1

  g2 = tf.Graph()
  with g2.as_default():
    with tf.Session() as sess:
      # y = A^x
      A = tf.constant([5, 7], tf.int32, name='A')

      x = tf.placeholder(tf.int32, name='x')

      y = tf.pow(A, x, name="y")

      print (sess.run(y, feed_dict={x: [3, 5]}))

      assert y.graph is g2

  default_graph = tf.get_default_graph()
  with tf.Session() as sess:
    # y = A + x
    A = tf.constant([5, 7], tf.int32, name='A')

    x = tf.placeholder(tf.int32, name='x')

    y = A + x
    print (sess.run(y, feed_dict={x: [3, 5]}))

    assert y.graph is default_graph


```

### Named Scopes

* named scopes are to categorize the computations in the tensor board graph so that it becomes easy for us to debug and understand the graph.

* without named scope the graph can go messy and complicated.

* you can also say that these are cetain blocks of code that you want to debug separatly using tensorboard

```
  import tensorflow as tf

  A = tf.constant([4], tf.int32, name='A')
  B = tf.constant([5], tf.int32, name='B')
  C = tf.constant([6], tf.int32, name='C')

  x = tf.placeholder(tf.int32, name='x')

  # y = Ax^2 + Bx + C
  with tf.name_scope("Equation_1"):
    Ax2 = tf.multiply(A, tf.pow(x, 2), name="Ax2")
    Bx = tf.multiply(B, x, name="Bx")
    y1 = tf.add_n([Ax2, Bx, C], name="calc_1")

  # y = Ax^2 + Bx^2
  with tf.name_scope("Equation_2"):
    Ax2 = tf.multiply(A, tf.pow(x, 2), name="Ax2")
    Bx2 = tf.multiply(B, tf.pow(x, 2), name="Bx2")
    y2 = tf.add_n([Ax2, Bx2], name="calc_1")

  with tf.name_scope("Final_Sum"):
    y = y1 + y2

  with tf.Session() as sess:
    print (sess.run(y, feed_dict={x: [10]}))

    writer = tf.summary.FileWriter('./tensorboard_file', sess.graph)
    writer.close()

```

### Write a Basic Linear Regression model

```
  import tensorflow as tf

  # Model parameters
  W = tf.Variable([0.3],dtype = tf.float32, name='var_W')
  b = tf.Variable([0.1],dtype = tf.float32, name='var_b')

  # Model input and ouput
  x = tf.placeholder(tf.float32)
  linear_model = W*x + b

  y = tf.placeholder(tf.float32)

  # define your loss function
  loss = tf.reduce_sum(tf.square(linear_model - y))

  # Define an optimizer which will try to optimize the algorithm
  optimizer = tf.train.GradientDescentOptimizer(0.01)

  train = optimizer.minimize(loss)

  # train  data

  x_train = [1,2,3,4]
  y_train = [0,-1,-2,-3]


  init = tf.global_variables_initializer()

  with tf.Session() as sess:
    sess.run(init)
    for i in range(1000):
      sess.run(train, {x:x_train, y:y_train})

      # Now evaluate the training accuracy
      curr_W, curr_b, curr_loss = sess.run([W,b,loss],{x:x_train, y:y_train})

    print("w:",curr_W)
    print("b:",curr_b)
    print("loss:",curr_loss)
    
```

## Image Recognition


* Every image is made up of millions of pixels which contains information like saturation, hue, grayscale etc.

* Each pixel holds a value based on the image, e.g wether it is a grayscale image or RGB

* in a colour image, every pixel is a RGB value(Redm Green, Blue)-- how mch each of these component is present in each pixel.

* Each of these values will be present from range 0-255. For example: Red pixel would be represented as [255,0,0]

* Grayscale images contains shades from white to black but no colour. In a gray scale image every pixel contain one value which is the intensity of that perticular pixel from range 0.0.-1.0.

* An image is nothing but a 2D matrix, that is x and y cordinates of each pixel in the screen, but in addition to it we also need to hold the pixel value as well.

* So the number of channel specifies the number of elements in the third dimension. In case of gray scale image the 3rd dimension will contain a single channel or single value while a coloured image will contains the 3rd dimension as the RGB value. 

* So that means shape of the image contains 2 values (val1,val2,val3), where val1 is width of the image and val2 is the height of the image and val3 is the number of channels for the image.


### Transposing an Image

* In this exercise we will read an image using tensorflow and then transpose it using tensorflow

```
  # Lets download an image to play with
  ! wget https://upload.wikimedia.org/wikipedia/commons/5/54/TaraxacumOfficinaleSeed.JPG
  ! wget https://www.planwallpaper.com/static/images/880665-road-wallpapers.jpg
  ! wget http://files.all-free-download.com//downloadfiles/wallpapers/2560_1600/at_the_beach_wallpaper_beaches_nature_1247.jpg
  ! wget https://wallpaper-house.com/data/out/1/wallpaper2you_12642.jpg
  
```

* Now that we have downloaded the images, lets write the code for transpose

```
  import tensorflow as tf
  import matplotlib.image as mp_img
  import matplotlib.pyplot as plot
  import os


  filename = "./TaraxacumOfficinaleSeed.JPG"

  image = mp_img.imread(filename)

  print ("image shape is:", image.shape)
  print ("image array:", image)

  plot.imshow(image)
  plot.show()

  x = tf.Variable(image, name='image')

  init = tf.global_variables_initializer()

  with tf.Session() as sess:
    sess.run(init)
    # Note that here in perm [1,0,2] we are swapping 0 and 1 indices or x with y
    transpose = tf.transpose(x, perm = [1,0,2])

    result = sess.run(transpose)

    print ("transposed image shape:", result.shape)

    plot.imshow(result)
    plot.show()
  
```

### Resizing image using tensorflow

#### Without tf.stack() method

```

  #@title
  import tensorflow as tf

  from PIL import Image

  original_image_list = ["./880665-road-wallpapers.jpg", 
                         "./TaraxacumOfficinaleSeed.JPG",
                         "./wallpaper2you_12642.jpg",
                         "./at_the_beach_wallpaper_beaches_nature_1247.jpg"]

  # Make a queue of file names including all the images specified.
  filename_queue = tf.train.string_input_producer(original_image_list)

  # Read an entire image file.
  image_reader = tf.WholeFileReader()

  with tf.Session() as sess:
      # Coordinate the loading of image files. It manages the thread in a queue
      coord = tf.train.Coordinator()
      threads = tf.train.start_queue_runners(sess=sess, coord=coord)

      image_list = [];
      for i in range(len(original_image_list)):
          # Read a whole file from the queue, the first returned value in the tuple is the
          # filename which we are ignoring.
          _, image_file = image_reader.read(filename_queue)

          # Decode the image as a JPEG file, this will turn it into a Tensor which we can
          # then use in training.
          image = tf.image.decode_jpeg(image_file)

          # Get a tensor of resized images.
          image = tf.image.resize_images(image, [224, 224])
          image.set_shape((224, 224, 3))

          # Get an image tensor and print its value.
          image_array = sess.run(image)
          print (image_array.shape)

          Image.fromarray(image_array.astype('uint8'), 'RGB').show()

          # The expand_dims adds a new dimension
          image_list.append(tf.expand_dims(image_array, 0))

      # Finish off the filename queue coordinator.
      coord.request_stop()
      coord.join(threads)

      index = 0

      # Write image summary
      summary_writer = tf.summary.FileWriter('./m4_example2', graph=sess.graph)

      for image_tensor in image_list:
          summary_str = sess.run(tf.summary.image("image-" + str(index), image_tensor))
          summary_writer.add_summary(summary_str)
          index += 1

      summary_writer.close()
      
```

* Visualize Tensorboard here : https://colab.research.google.com/drive/1ndNCQmID2x7Gk_gNGer2k4yz4EJ1ZuG0

* Tensor flow often deals with list of images in 4-D tensor, with the first dimension as the number of the images in that list. For example (10[number of images], 6[width], 6[height], 3[number of channels])
 
* For the Images to be represented as 4D tensors, all images should have the same size.

#### With tf.stack() method

* this method is used to transform a tensor of rank r to a tensor of rank r+1 tensor
* we will run the same above code using tf.stack() method

```
  #@title
  import tensorflow as tf

  from PIL import Image

  original_image_list = ["./880665-road-wallpapers.jpg", 
                         "./TaraxacumOfficinaleSeed.JPG",
                         "./wallpaper2you_12642.jpg",
                         "./at_the_beach_wallpaper_beaches_nature_1247.jpg"]

  # Make a queue of file names including all the images specified.
  filename_queue = tf.train.string_input_producer(original_image_list)

  # Read an entire image file.
  image_reader = tf.WholeFileReader()

  with tf.Session() as sess:
      # Coordinate the loading of image files. It manages the thread in a queue
      coord = tf.train.Coordinator()
      threads = tf.train.start_queue_runners(sess=sess, coord=coord)

      image_list = [];
      for i in range(len(original_image_list)):
          # Read a whole file from the queue, the first returned value in the tuple is the
          # filename which we are ignoring.
          _, image_file = image_reader.read(filename_queue)

          # Decode the image as a JPEG file, this will turn it into a Tensor which we can
          # then use in training.
          image = tf.image.decode_jpeg(image_file)

          # Get a tensor of resized images.
          image = tf.image.resize_images(image, [224, 224])
          image.set_shape((224, 224, 3))

          # Get an image tensor and print its value.
          image_array = sess.run(image)
          print (image_array.shape)

          # Convert a numpy array of kind(224,224,3) to a tensor of shape (224,224,3)
          image_tensor = tf.stack(image_array)

          # The list will now simply holds the image tensor
          image_list.append(image_tensor)

      # Finish off the filename queue coordinator.
      coord.request_stop()
      coord.join(threads)

      # now lets convert all tensors to a  single tensor of 4-d using stack() command
      # 4 images can be accessed with 4-D tensor as (0,224,224,3), (1,224,224,3),etv

      image_tensor = tf.stack(image_list)
      print(image_tensor)


      summary_writer = tf.summary.FileWriter('./example_4', graph = sess.graph)

      # write all images in a one go

      summary_str = sess.run(tf.summary.image("images",image_tensor,max_outputs=4))
      summary_writer.add_summary(summary_str)   

      summary_writer.close()
      
```

## Using K- Nearest Neighbors for digit recognition

* Will introduce the MNIST handwritten datasets

* Understand KNN machine learning algorithm

* Implement KNN algo to detect handwritten digits from 0-9


#### MNIST

* MNIST  is a handwrtten digit database or dataset.
* it stands for Modifies National Institute of standards and technology
* each image in the dataset is a grayscale image
* you can download the dataset from [link](http://yann.lecun.com/exdb/mnist/) 
* every image has size (28,28), which gives 784 pixels in each image.
* since it is a single channel it contains the intensity


#### KNN

* It is a supervised machine learning algorithm which uses the training data to find what is similar to the current sample.

*  It uses the entire dataset as its model.

* Each element in the dataset have a label attached to it.

*  When a new input is feeded KNN tries to find the most similar image in the dataset.

* it does so using distance measurements, i.e how far away one data point is from another data point.

* most of the distance measurements are like euclidean distance, hamming distance(remember Networking :D), etc

![Image](https://github.com/Gaurav-Pande/MLCC/blob/master/tensorflow_basics/assets/2.png)

##### Distance Measures:
 
 * euclidean distance. it is like a displacement, i.e join directly two points and find the distance.
 
 ![Image](https://github.com/Gaurav-Pande/MLCC/blob/master/tensorflow_basics/assets/3.png)
 
 * with grayscale images we use L1 distance(snake distance): 
 
 ![Image](https://github.com/Gaurav-Pande/MLCC/blob/master/tensorflow_basics/assets/4.png)
 
 * you can observe that euclidean is more shorter than L1.
 
### KNN implementation steps:

1.  Getting MNIST images from dataset and test images in batches to tensorflow libraries

2.  Calculating L1 distance(find the distance between test digit and all training digits)

3.  Running algorithm:  Predict labels of all test data and measure accuracy.


```
  import numpy as np
  import tensorflow as tf

  # Import MNIST data
  from tensorflow.examples.tutorials.mnist import input_data

  # Store the MNIST data in mnist_data directory
  # remember here the one_hot=True means that label will be represented a vector
  # of 10 elements, so for example, 4 will be represented as
  # [0,0,0,0,1,0,0,0,0,0] (note that 4 is at the index 4 of the list)

  mnist = input_data.read_data_sets("mnist_data/", one_hot=True)

  training_digits, training_labels = mnist.train.next_batch(5000)
  test_digits, test_labels = mnist.test.next_batch(200)

  # we have no idea how many images we are going to pass in,so first param in the 
  # placeholder [None, 784] indicates the index of the image, and the second 
  # parameter in 784 indicates vector of 784 values, because we represent the images
  # as a vector.
  training_digits_pl = tf.placeholder("float", [None, 784])

  test_digit_pl = tf.placeholder("float", [784])

  # Nearest Neighbor calculation using L1 distance
  l1_distance = tf.abs(tf.add(training_digits_pl, tf.negative(test_digit_pl)))

  distance = tf.reduce_sum(l1_distance, axis=1)

  # Prediction: Get min distance index (Nearest neighbor)
  pred = tf.arg_min(distance, 0)

  accuracy = 0.

  # Initializing the variables
  init = tf.global_variables_initializer()

  with tf.Session() as sess:
      sess.run(init)

      # loop over test data
      for i in range(len(test_digits)):
          # Get nearest neighbor
          nn_index = sess.run(pred, \
            feed_dict={training_digits_pl: training_digits, test_digit_pl: test_digits[i, :]})

          # Get nearest neighbor class label and compare it to its true label
          print("Test", i, "Prediction:", np.argmax(training_labels[nn_index]), \
              "True Label:", np.argmax(test_labels[i]))

          # Calculate accuracy
          if np.argmax(training_labels[nn_index]) == np.argmax(test_labels[i]):
              accuracy += 1./len(test_digits)

      print("Done!")
      print("Accuracy:", accuracy)

```


Hope you have enjoyed My notes.

I learned all this from a pluralsite tutorial. [link](https://www.pluralsight.com/courses/tensorflow-understanding-foundations)
  
  
