# Neural 3D Mesh Renderer (2018) 
### Summary
* Use polygon meshes to sample photos
	* Polygon meshes are efficient, allow textures, and are scalable
* Problem: rasterization prevents back-propagation because it’s discrete (non-differentiable maybe??)
* Solution: use an approximate gradient

####  3D representations in neural networks
* 3D representations are either:
	* Rasterized (voxels, RGB images)
		* Can be processed by CNNs
	* Geometric (Point cloud, polygon mesh, primitive sets)

#### Single-image 3D reconstruction
* Reconstructing 3D structures from (2D) images is a cool hot topic in computer vision rn
* Before this paper:
	* Voxels usually
	* PTN (Perspective transformer nets) learning 3D structures using silhouette images
	* Models learn 2D to 3D mapping using ground truth 3D models


### Approximate gradient and neural renderer
#### Rendering pipeline and its derivative
1. Start with 3D mesh with N vertices and N faces
2. Transform from object to screen space to render
3. Generate image from vertices and faces via sampling


#### Things to look up
* DeepDream
* PTN
* More of this rasterization vertex math shit
* 	* do they get smooth training data to get their differentiable rasters?? What does this look like
	* Why are we using backpropagation in the renderer (or rasterization step??
