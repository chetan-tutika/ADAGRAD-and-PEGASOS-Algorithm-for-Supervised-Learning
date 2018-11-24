# ADAGRAD-and-PEGASOS-Algorithm-for-Supervised-Learning

To implement ADAGRAD-and-PEGASOS-Algorithm to categorize articles into their respective topics<br />
DataSet used - RCV1 Dataset
<br />

## PEGASOS IMPLEMENTATION
Initialize all weights(w) to zero. Size of the weight parameter is 47236x1, i.e. equal to the number of
features for each article<br />
Update ‘w’ upto ‘i’ iterations w.r.t to the computed gradient<br />
Update value determination:<br />
Choose a subset of B data points form the training set<br />
Compute the predicted value of the selected data points with the current w. Select the points, labels
with values (label<predicted value>) < 1<br />
Compute the gradient on the selected false prediction points. Update the weights based on the
computed gradient and the update value(neta)<br />
Calculate projected value of the new calculated ‘w’ and update according to the projection
Repeat for ‘i’ iterations<br />
Initialization:<br />
Number of iterations = 100<br />
Batch size = 1000<br />
Regularization parameter ‘neta’ = 0.0000010
<br />
  
### Results
#### Training error vs no. of iterations for different regularization parameters
![image](https://user-images.githubusercontent.com/41950483/48972829-caed0f80-f000-11e8-8cd5-ce977e5186dc.png)<br />
it can be observed that very high values of the regularization parameter results in almost
zero update in the error. This is since the loss converges to the minimum at a very low pace such that
the convergence is almost zero.<br />
Very low values of the regularization parameter such as 1e-08 will increase the step size of the update to
a very high value. This will result in missing the global minimum of the loss function which results in the
oscillation of the loss.<br />
The regularization value of 1e-06 is optimal for our solution since it converges quickly to the global minimum and gives the least error while compared to the other values<br />
<br />
#### Training error vs no. of iterations for different batch sizes
![image1_pegasos_b_variation_latest](https://user-images.githubusercontent.com/41950483/48972998-15bc5680-f004-11e8-9abb-ebeb83dadd5a.png)<br />
The batch size approximates all the points in the data set and gives an expectation of the loss is comparable to the loss
acquired by gradient descent.<br />
While a batch size of 3000 gives low error an converges quickly, we can also observe that a batch size of
1000 gives equally good results. Taking the batch size to be as low as possible will ensure that the
process of updating our weights is not computationally expensive. Since the batch size of 3000 and 1000
both give better results than other sizes, it is advisable to use a batch size of 1000<br />
</ br>
## ADAGRAD Implementation
Initialize all weights(w) to zero. Size of the weight parameter is 47236x1, i.e. equal to the number of
features for each article. Initialize the transformation matrix ‘G’ as an identity matrix<br />
Update ‘w’ upto ‘i’ iterations w.r.t to the computed gradient and the transformation matrix<br />
Update value determination:<br />
Choose a subset of B data points form the training set<br />
Compute the predicted value of the selected data points with the current w. Select the points, labels
with values (label<predicted value>) < 1<br />
Compute the gradient on the selected false prediction points. Update the value of the weights based on
the Mahala Nobis norm<br />
Compute the updated value of the transformation matrix G<br />
Repeat the process for ‘i’ iterations<br />
Initialization:<br />
Number of iterations = 100<br />
Batch size = 1000<br />
Regularization parameter ‘neta’ = 0.0000010<br />
<br />
  
### Results
#### Training error vs no. of iterations for different regularization parameters
![image_adagrad_lambda_variation](https://user-images.githubusercontent.com/41950483/48973009-4d2b0300-f004-11e8-83be-8fdae49de7c7.png)<br />
Very high values of the regularization parameter results in almost zero update in
the error. This is since the loss converges to the minimum at a very low pace such that the convergence
is almost zero<br />
Very low values of the regularization parameter such as 1e-15 will increase the step size of the update to
a very high value. This will result in missing the global minimum of the loss function which results in the
oscillation of the loss<br />
The regularization value of 1e-08 is optimal for our solution since it
converges quickly to the global minimum and gives the least error while compared to the other values<br />
#### Training error vs no. of iterations for different batch sizes
![image_adagrad_b_variation](https://user-images.githubusercontent.com/41950483/48973010-5025f380-f004-11e8-9856-1ed1f7ed987d.png)<br />
The batch size approximates all the points in the data set and gives an expectation of the loss is comparable to the loss
acquired by gradient descent<br />
While a batch size of 3000 gives low error an converges quickly, we can also observe that a batch size of
1000 gives equally good results. Taking the batch size to be as low as possible will ensure that the
process of updating our weights is not computationally expensive. Since the batch size of 3000 and 1000
both give better results than other sizes, it is advisable to use a batch size of 1000
