# 3D_SMLM_visualization

SMLM datasets are point clouds in 2D or 3D space (list of coordinates).
The most suitable way of visualizing this kind of data is the density-colored scatter plot.
This is however computationally challenging as one need to compute the density at each single point (or localization).   
```matlab
scatter3(x, y, z, 1, color_vector, '.');
```
where `x`, `y`, `z` and `color_vector` are all Nx1 vectors and `color_vector` represents the density at each (x,y,z) coordinate.  

In this project, I computed the density at each single point (localization) by computing the sum of the exponential distances of the point of interest to all the other points (localization).
The direct computation of these distances, however, is very time consuming especially for very large point clouds or SMLM data (>1000).

In order to speed-up the computational time, I used the Fast Gauss Transform in order to compute all pair-wise distances. This is followed by summing up all distances for the localization of interest.

For Fast Gauss Transform, I used the following implementation which has a MATLAB wrapper that can easily be compiled (It worked for me with MATLAB 2015-2017).
https://github.com/vmorariu/figtree

Once you download the above library and compiled the required mex files, you can run script.m in order to visualize 3D SMLM datasets.