Author : ADHITHIYA MS

Objective:
The main goal of this project is to take a set of (x, y) data points from the xy_data.csv file and find the best parameters (θ, M, X) for a complex parametric curve that fits this data. The "best fit" is the one that minimizes the total error between the curve and the actual data points.

Problem statement:
I'm fitting the 1500 data points to the following parametric equations, which are all functions of a parameter t (a vector of 1500 points spaced from 6 to 60):

How the "Best Fit" is Measured:
To find the best-fitting curve, I needed to minimize the error. I used the Sum of Absolute Error (SAE), or L1 Loss, which is simply the total sum of the individual differences between the actual data and the curve's predicted values. The function I'm minimizing is: 

Error = Σ ( |x_actual - x_predicted| + |y_actual - y_predicted| )

Methodology:
The entire process is contained in the ADHITHIYA_FLAM_Assignment.ipynb Google collab. First, the script loads the xy_data.csv file into a pandas DataFrame. Then, I defined a Python function (get_the_error) that takes the parameters (θ, M, X), calculates the predicted x and y values based on the equations above, and returns the total SAE. The core of the project is the scipy.optimize.minimize function. I used it to find the parameters that result in the lowest possible error.For the method, I chose L-BFGS-B. It's a great quasi-Newton method for this kind of problem because it's efficient and lets me set "box constraints" (bounds) for the parameters.My p0 for the parameters was [θ=25.0, M=0.0, X=50.0].

The bounds I set were:
θ: (0, 50)
M: (-0.05, 0.05)
X: (0, 100)

Finally, I used matplotlib to plot the original data as a scatter plot and then overlaid my fitted curve as a line plot. This provides a clear visual check to see how well the optimization worked.

How to Run This Project:
Make sure you have the necessary Python libraries (see dependencies below). Place the xy_data.csv file inside a sub-folder named Data/. (If you place it elsewhere, you'll need to update the path in Step 2 of the notebook). Open and run all the cells in the ADHITHIYA_FLAM_Assignment.ipynb notebook.

Dependencies:
You'll need the following libraries. You can install them all using pip:

Bash

pip install pandas numpy scipy matplotlib