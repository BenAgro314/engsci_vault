TARGET DECK: Main Deck


 
 How is correspondance generalized in ICP? (hint: matrix) #fc 
 $$\min_{X \in SE(3)} \sum_i \sum_j C_{ij} ||X^Op^{m_j} - p^{s_i}||^2$$
 where $C_{ij}$ is a matrix of ones and zoers that maps from the scene points to the model points. 
<!--ID: 1621985215450-->


Pose estimation as optimization given known corrispondances. You are given ${}^Op^{m_i}$, the points on the model with repect to the object frame, ${}^Vp^{S_i}$, points in the scene with respect to the camera frame, and know that these *correspond to the same points*. #fc
We want to solve the optimization problem
$$\min_{R^O, p^O} \sum_{i = 1}^{N} ||p^O + R^O\;{}^Op^{m_i} - X^C\;{}^Cp^{s_i}||^2$$ subject to the constraints $$R^T = R^{-1}$$ and $$\det R = 1$$
<!--ID: 1621638423181-->



What conditions does a rotation matrix have to satisfy? #fc 
$$R^T = R^{-1}$$ and $$\det R = 1$$
<!--ID: 1621638423198-->


2 by 2 rotation matrix in terms of $\theta$ #fc
$$\begin{bmatrix}\cos\theta  & -\sin\theta\\
\sin\theta & \cos\theta \end{bmatrix}$$
<!--ID: 1621638423201-->


What does ICP stand for? #fc 
ICP is the iterative closest point algorithm.
<!--ID: 1621638423204-->


What is ICP used for? #fc
To find the correspondances between the points in the frame of the model $$p^{m_i}$$ and the points seen by the camera $$p^{s_i}$$
<!--ID: 1621638423207-->


What is the ICP algorithm (2 steps)? #fc 
Estimate the object pose, $\hat{X}^O$, and then
find the point on the model that is closest in euclidan distance to the transformed scene points (using that estimated pose):
$$\forall i; \hat{c}_i = \text{argmin}_{j\in N_m} ||\hat{X}^O\;{}^Op^{m_{c_i}} - p^{s_i}||^2$$
With this estimated correspondance, find a new $\hat{X}^O$, and *iterate*.
<!--ID: 1621638423210-->


What are model points $m_i$? #fc 
A point cloud on a models surface with repect to the model coordinates:
 $${}^Op^{m_i}$$
 
 
 What are scene points $s_i$? #fc 
 Points in the world frame gathered from a camera or lidar:
 $${}^Wp^{s_i}$$
 
 
 What is the goal of geometric pose estimation? #fc 
 To estimate the pose of an object: 
 $${}^WX^O$$
 
 
 What are corrispondances in geometric pose estimation? What does the notation $c_i = j$ represent? #fc 
 A mapping from the scene points to the model points. 
 $c_i = j$ means that scene point $i$ matches model points $j$.
 
 
 What does RANSAC stand for? #fc 
 Random Sample Consensus 
 
<!--ID: 1621985215529-->
