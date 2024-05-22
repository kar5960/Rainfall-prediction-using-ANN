# Rainfall-prediction-using-ANN
Predicting daily rainfall with help of ANN and other advance AI model.

Data Handling

We have taken the data from the IMD Pune website which is a public and reliable source of daily rainfall data in India. The data we have taken is gridded 0.25*0.25. The data here is rain gauge-based data and the whole methodology involves taking data for 1900-2010 from approximately 7000 rain gauges stations varied accordingly in country. Before quality checking and interpolation of the station rainfall data, verification of the location information of the station and checking of coding and typographic errors in the data were carried out. After applying the standard quality control tests such as tests for typing and coding errors, missing data, duplicate station check, extreme value check etc. on the daily station point rainfall data, the data were interpolated at fixed spatial grid points of 0.25° × 0.25° resolution. A common approach used for converting station rainfall data into grid point data is the spatial interpolation, which assumes that spatially distributed station rainfall values are spatially correlated or that the stations, which are close together tend to have similar rainfall characteristics. In this study, the grid point rainfall data at different resolutions have been used for preparing the daily rainfall over various spatial regions. The daily rainfall over a given region was computed as the area weighted rainfall over all the grid boxes over the region. The area weight assigned to each grid box was taken as the fractional grid box area enclosed by the outer boundaries of the reference region multiplied by a cosine factor (the cosine of the latitude of the centre point of the grid box). The cosine factor is required to account for the convergence of the meridians which lessens the impact of high-latitude grid points that represent a small area of the globe



 

The data taken from IMD was in netCDF file format, we converted the data into CSV file format and analyzed the variables in the file which were Rainfall, Latitude, Longitude, and Time. We made use of various Python libraries to convert the data into CSV format. The data was given for the whole country so to find data for particular coordinates we applied a simple greedy algorithm that took the distance(squared difference) between the given coordinates and all the coordinates that we have in our data and then we took the coordinates for which the distance was minimum. Now with the help of other Python libraries, we made an animation in which rainfall was depicted as a heat map for a year. For this, the library asked us to mark a rectangular area for which upper right and lower left coordinates were only required.


  








Artificial Neural Network

An Artificial Neural Network (ANN) is a computational model inspired by the human brain’s neural structure. It consists of interconnected nodes (neurons) organized into layers. Information flows through these nodes, and the network adjusts the connection strengths (weights) during training to learn from data, enabling it to recognize patterns, make predictions, and solve various tasks in machine learning and artificial intelligence.



 

There are multiple layers in ANN which are input , hidden and output layer.



Mathematics of ANN

 
The first layer contains all the input nodes for example a picture can be described as a combination of pixels which can be the input layer. Now we choose how many nodes we want in the second hidden layer and we do wights*f(x)+bias to calculate the second layer nodes, each node in 1 layer is linked to each node in 2 layers by some weight and every node in 2 layer has a bias. Initially, the weights are randomly chosen but they are optimized as the model runs. The loss matrix is the squared sum of the predicted value and actual value and after every iteration, we try to minimize the cost matrix by manipulating weights and biases. We use a technique called gradient descent to minimize the matrix and taking a derivative is a cumbersome task here as we have millions of data points.

Gradient descent-
Gradient descent algorithm does not work for all functions. There are two specific requirements. A function has to be:
•	differentiable
•	convex
First, what does it mean it has to be differentiable? If a function is differentiable it has a derivative for each point in its domain — not all functions meet these criteria. First, let’s see some examples of functions meeting this criterion:
 
Next requirement — function has to be convex. For a univariate function, this means that the line segment connecting two function’s points lays on or above its curve (it does not cross it). If it does it means that it has a local minimum which is not a global one.
Mathematically, for two points x₁, x₂ laying on the function’s curve this condition is expressed as:
 
where λ denotes a point’s location on a section line and its value has to be between 0 (left point) and 1 (right point).
In the case of a univariate function, it is simply the first derivative at a selected point. In the case of a multivariate function, it is a vector of derivatives in each main direction (along variable axes). Because we are interested only in a slope along one axis and we don’t care about others these derivatives are called partial derivatives.
Gradient Descent Algorithm iteratively calculates the next point using gradient at the current position, scales it (by a learning rate) and subtracts obtained value from the current position (makes a step). It subtracts the value because we want to minimise the function (to maximise it would be adding). This process can be written as:
 
There’s an important parameter η which scales the gradient and thus controls the step size. In machine learning, it is called learning rate and have a strong influence on performance.
We use an activation layer at every layer which can be of various types they help us to make the data unbiased and smoothen the data. We also use an optimizer so that our model avoids overfitting and converges quickly. 
