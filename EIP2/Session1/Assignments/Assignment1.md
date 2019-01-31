EIP 2 Assignment1

## Convolution

> Convolution is an operation to extract specific feature or characteristic from the input image.

It is a way to mix two functions.In machine learning ,during convolution only specific region of the image is processed at a time(area of this region depends on the size of kernel) and this operation is repeated until all the pixels of image are covered.

![Convolution of 7 x 7 image and 3 x 3 kernel](https://raw.githubusercontent.com/iamaaditya/iamaaditya.github.io/master/images/conv_arithmetic/full_padding_no_strides_transposed.gif)

Mathematically,

1. Convolution of continuous signal

$$
{\begin{aligned}
(f*g)(t)& =  \int _{-\infty }^{\infty }f(\tau )g(t-\tau )\,d\tau \\
&=\int _{-\infty }^{\infty }f(t-\tau )g(\tau )\,d\tau 
\end{aligned}}
$$



2.Discrete Convolution
$$
\begin{aligned}(f*g)[n]&=\sum _{m=-\infty }^{\infty }f[m]g[n-m]\\
&=\sum _{m=-\infty }^{\infty }f[n-m]g[m]
\end{aligned}
$$

We can consider $f$ as input image and $g$ as kernel or vice-versa.To add a new layer we perform convolution on the previous layer with the kernel.We use discrete convolution in machine learning.

![Convolution in image processing](https://i1.wp.com/timdettmers.com/wp-content/uploads/2015/03/convolution.png)



## Filters / Kernels

> Filter / kernel is a matrix used to extract a specific feature from the input image or to perform a specific task on image .It is also called as *feature extractor*.

 The feature can be edge,color etc. and the task can be blurring or sharpening image etc. The task is achieved by convolving image using filter.The value of the kernel matrix is specific to each task and the resulting output image thus depends on the kernel.The kernel can be of any size but `3 x 3 ` is most commonly used for feature extraction `1 x 1` is mainly used for dimensionality reduction. 

![Kernel1](https://i1.wp.com/timdettmers.com/wp-content/uploads/2015/03/convolution.png)

![Kernel2](https://i1.wp.com/timdettmers.com/wp-content/uploads/2015/03/convolution_quiz.png)

## 1$\times$1 Convolution

1x1 convolution at a given time processes only one pixel.This can be used to reduce the number of channels(thereby dimensionality ).This is done in order to keep only relevant features. Reduced dimensionality also results in decreased computational cost.

Consider a `400 x 400 , 64 ` image convolving with `1 x 1 , 8` kernel (actually `[1 x 1 x 64], 8`)

the resulting image is `400 x 400 , 8` .Thus, the number of channels shrink but the resolution is preserved.

![Convolution with Kernel of size 1x1](https://raw.githubusercontent.com/iamaaditya/iamaaditya.github.io/master/images/conv_arithmetic/full_padding_no_strides_transposed_small.gif)



## 3$\times$3 Convolution

This is the most widely used convolution and is almost the default kernel size.Larger kernels can be constructed by using multiple 3 $\times$ 3 convolutions.For instance: two  3 $\times$  3 makes a 5 $\times$ 5 kernel,three  3 $\times$ 3 kernel makes a 7 $\times$ 7 and so on.The computation is complex when dealing with larger kernels the same computation becomes simple if we use  3 $\times$ 3 multiple times instead of a larger kernel. 

The image resulting after performing  3 $\times$3 convolution will have resolution reduction of 

`(z - 2) X (z - 2)` given the input image's resolution is `z X z`.

## Epoch 

> *"Epoch defines the **number of times the entire training dataset is processed** to train the neural network."*

After every epoch the weights are updated. The value of epoch is dependent on the problem at hand and the accuracy required.

Epochs are hyper-parameters and are comprised of one or more batches.

It is an integer and it's value is usually large.For Ex-100,500,1000 etc.



## Feature Map

> It is the output image resulting after performing convolution on an image using a kernel.It is also called as *activation map.*

$$
feature map = input \circledast kernel
$$
In CNN,each feature map will have specific and unique feature depending on the kernel values and is obtained by convolving previous layer with the corresponding kernel.Each feature map belong to separate channel.

![feature map](https://i1.wp.com/timdettmers.com/wp-content/uploads/2015/03/convolution_quiz.png)



## Feature Engineering

> It is a process of using existing data and transforming it to create features that are relevant and useful  to improve the accuracy of predictive models.

Good features often yield good models.It is a manual  and iterative process.After each iteration usefulness of the feature in prediction is tested and if more relevant or useful feature is found we omit the less useful feature.

The process involves following steps:

1.Brainstorm features : Extract all the possible features. 

2.Devise features : Decide and shortlist which all features would be useful to solve the problem at hand.

3.Select features : Select the features based on various feature selection methods that provide different views to your model (try to select independent variables as far as possible) and remove redundant features.

4.Evaluate Model :Using different dataset test for the accuracy of the model. 



## 10 Examples of Mathjax in Markdown

For `display` mode type the formula in this format -> "`$$[Type formula heere] $$`"

**1.Summation**

To display sum  :


$$
\sum_{i = 0}^n i^3 = \frac{n^2(n + 1)^2}{4} = \left[ \sum n \right] ^ 2
$$
Type  `\sum_{i = 0}^n i^3 = \frac{n^2(n + 1)^2}{4} = \left[ \sum n \right] ^ 2`



**2.Matrix**

To display matrix as shown:
$$
\begin{bmatrix} 
		1 & x^2 & x^3 \\ 
		10 & y^2 & y^4 \\
        6 & z & z^5\end{bmatrix}
$$
Type

```
 \begin{bmatrix} 
  1 & x^2 & x^3 \\ 
  10 & y^2 & y^4 \\
  6 & z & z^5\\
  \end{bmatrix} 
```

replace the  `bmatrix` with `pmatrix` to view the values as shown 
$$
\begin{pmatrix} 
		1 & x^2 & x^3 \\ 
		10 & y^2 & y^4 \\
        6 & z & z^5\\
        \end{pmatrix}
$$


**3.Standard Deviation**
$$
\sigma = \sqrt{ \frac{1} {N} \sum_{i=1}^N (x_i -\mu)^2}
$$
type:

`\sigma = \sqrt{ \frac{1}{N} \sum_{i=1}^N (x_i -\mu)^2}`

**4.Normal Distribution**
$$
f(x) = \int_{-\infty}^{\infty} \frac{x^2}{\sqrt{2\pi{\sigma}^2}}e^{-\frac{(x - \mu)^2}  {2\sigma ^2}} = \sigma^2
$$


```
f(x) = \int_{-\infty}^{\infty} \frac{x^2}{\sqrt{2\pi{\sigma}^2}}e^{-\frac{(x - \mu)^2}  {2\sigma ^2}} = \sigma^2
```

**5.Trigonometric Equation**
$$
tan\frac{\phi}{2} = \pm \sqrt{\frac{1-cos\phi}{1 + cos\phi}}
$$
`tan\frac{\phi}{2} = \pm \sqrt{\frac{1-cos\phi}{1 + cos\phi}}`

**6.Ampere's Circuital Law **
$$
\begin{align}\tag1
\oint _C\mathbf{\vec{B}}\cdot \vec{d\mathbf{l}} = \iint_S\left(\mu_0\vec{\mathbf J} + \mu_0\epsilon_0\frac{\partial \mathbf{\vec E}}{\partial t} \right) \\[2ex]  \tag2 
\nabla \times  \vec{ \mathbf{B}} = \mu_0 \vec {\mathbf{J}} + \mu_0 \epsilon_0 {\partial \vec{\mathbf{E}} \over \partial t}
\end{align}
$$

```
\begin{align}\tag1
\oint _C\mathbf{\vec{B}}\cdot \vec{d\mathbf{l}} = \iint_S\left(\mu_0\vec{\mathbf J} + \mu_0\epsilon_0\frac{\partial \mathbf{\vec E}}{\partial t} \right) \\[2ex]  \tag2 
\nabla \times  \vec{ \mathbf{B}} = \mu_0 \vec {\mathbf{J}} + \mu_0 \epsilon_0 {\partial \vec{\mathbf{E}} \over \partial t}
\end{align}
```

**7.ReLU**
$$
f(x) = \begin{cases}
		x & \text{if $x$}\geq 0 \\[2ex]
		0 & \text{if $x$} < 0\\[2ex]
		\end{cases}
$$

```
f(x) = \begin{cases}
		x & \text{if $x$}\geq 0 \\[2ex]
		0 & \text{if $x$} < 0\\[2ex]
		\end{cases}
```



**8.**
$$
\begin{align}
(x + y)^2 & = (x + y)(x + y)\\
& = x(x + y) + y(x + y) \\
&= x^2 + xy +yx +y^2 \\
&= x^2 +2xy +y^ 2
\end{align}
$$

```
\begin{align}
(x + y)^2 & = (x + y)(x + y)\\
& = x(x + y) + y(x + y) \\
&= x^2 + xy +yx +y^2 \\
&= x^2 +2xy +y^ 2
\end{align}
```





**9.Infinite product series of $\pi$ ** 



$1.$François Viète's infinite series

$2.$ John Wallis' Infinite series 
$$
\begin{align}
& \frac{2}{\pi} = \frac{\sqrt{2}}{2}\cdot\frac{\sqrt{2 + \sqrt{2}}}{2}\cdot \frac{\sqrt{2+\sqrt{2+\sqrt{2}}}}{2}\cdots \tag 1\\[2ex]  
&\frac{\pi}{2} = {2 \over 1}\cdot{2 \over 3}\cdot{4 \over 3}\cdot{4 \over 5}\cdot{6 \over 5}\cdot{6 \over 7}\cdot{8 \over 7}\cdot{8 \over 9}\cdots=\prod_{n = 1}^{\infty}\frac{4n^2}{4n^2-1}\cdot \tag2
\end{align}
$$




```
\begin{align}
& \frac{2}{\pi} = \frac{\sqrt{2}}{2}\cdot\frac{\sqrt{2 + \sqrt{2}}}{2}\cdot \frac{\sqrt{2+\sqrt{2+\sqrt{2}}}}{2}\cdots \tag 1\\[2ex]  
&\frac{\pi}{2} = {2 \over 1}\cdot{2 \over 3}\cdot{4 \over 3}\cdot{4 \over 5}\cdot{6 \over 5}\cdot{6 \over 7}\cdot{8 \over 7}\cdot{8 \over 9}\cdots=\prod_{n = 1}^{\infty}\frac{4n^2}{4n^2-1}\cdot \tag2
\end{align}
```



**10.Direction Ratios**
$$
tan \theta = \frac{\sqrt{\sum (m_1n_2 - m_2n_1)^2}}{l_1l_2+m_1m_2+n_1n_2}
$$
`tan \theta = \frac{\sqrt{\sum (m_1n_2 - m_2n_1)^2}}{l_1l_2+m_1m_2+n_1n_2}`



## Activation Function

> Activation function decides the contribution of a node to the succeeding or output layer.

It introduces non-linearity to the network and is a vital part of backpropagation.A node receives inputs from several other nodes or neurons in the previous layer and comes up with a weighted sum.Based on this value the activation function decides whether a neuron is to be activated or not.If a neuron's contribution is a cause of error( for instance in over fitting) then that neuron is not activated by the activation function during back-propagation.

Some examples of activation functions are ReLU,Sigmoid,TanH etc.

![Activation Function](https://www.researchgate.net/profile/Alfredo_Rosado/publication/220348493/figure/fig1/AS:305593156947975@1449870494897/Scheme-of-a-neuron-and-an-MLP-ANN.png)

## Receptive Field

Receptive field is the region on the output layer a neuron in the kernel is connected to.

Global receptive field is the overall view from the from 1st layer to the final layer of the CNN.

![](https://mlblr.com/images/ReceptiveField.gif)

In the above figure we see the local receptive field at 1 $\times$ 1 layer is 3 $\times$ 3 and the local receptive field at       3 $\times$ 3 layer is also 3 $\times$ 3,but the global receptive field at 1 $\times$ 1 is 5 $\times$ 5.Every time we add a layer the receptive field field increases by 2 $\times$ 2(given that we are using a 3 $\times$ 3 kernel).

## How to upload a Project on GitHub

These are the steps to upload a project to GitHub using Web UI.

**Steps:**  

1. Goto https://github.com/ 

2. `Signin` to your account or if you are new to GitHub `Signup` and create a new account by filling the required details.

3. Click on $+$ icon at the (second icon at the top right side). Select `New Repository`.

4. Fill the all details : 
   - Type the repository name of your choice . For ex-`myFirstRepo`
   - Briefly describe about the project in `Decription` box.(This step is optional)
   - Select `Public` radio-button.
   - Initialize README file.(optional.But it is a good and conventional procedure)
   - Select `programming language` and `licence`. (optional)

5. Select the desired repository(here `myFirstRepo` ) and in `<>code` section 
   - Select `Create  new file` to create a file online using Web UI.
   - Click on`upload files` to upload from local machine(your desktop).You can either use "Drag and Drop" option or select `choose your files` .
   - Under the 'Commit Changes' section explain the changes you made and the extended description.
   - Choose 'Commit directly to the **master** branch.' to make the changes directly int original master branch and press `Propose changes` . 
   - Or Choose "Create a **new branch** for this commit and start a pull request."  press `Propose changes` . Then write briefly about the pull request and press `Create pull request` . 
   - If you want to merge the pull request then go to `Pull Requests` section and select the desired "pull request" and click on `Merge Pull request` and then click on `Confirm merge`.Write about the merge in the comment section.

6. If you want to work on your local machine press `Clone or download` and select any one of the `openin Desktop`(use GitHub Desktop to work) or `Download ZIP`. 

