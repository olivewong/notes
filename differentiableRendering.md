# Differentiable rasterization

## Neural 3D Mesh Renderer (2018) 
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

## DIB-R: Learning to Predict 3D Objects with an Interpolation-based Differentiable Renderer
- A cool new way to create 3D objects from 2D images

### Links
- [This Neural Network Creates 3D Objects From Your Photos](https://www.youtube.com/watch?v=548sCh0mMRc)
- [DIB-R](https://nv-tlabs.github.io/DIB-R/)

### Intro
- A photo is a 2D representation of 3D reality
- Humans know this - we see a pic of a cube and know it's 3D and can imagine what the other angles would look like
- But how can a model do this?

#### The shiny new neural network
- This model guesses 3 things from a (2D) input image:
    1. Mesh (the shape)
    2. Lighting (what configuration to get the look in the photo)
    3. The texture map
- We plug this^, and a camera position to a program `DIB-Renderer`, it can render from that camera position (reconstruct the geometry, lighting, and textures in a new photo)

### Example use cases
- If we have a photo of a bird, it can generate photos of the bird spinning
- Can improve depth perception of robots
- Can be used to generate 3D assets (not perfect but someone can fill in the details)

#### Results
- Beats CMR (older technique for ) - details are much nicer and more realistic

