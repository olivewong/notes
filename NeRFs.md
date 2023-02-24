# Paper notes: NeRF - Neural Radiance Fields
## Links:
- [Vid explanation](https://www.youtube.com/watch?v=CRlN-cYFxTk)
- [Paper](https://arxiv.org/abs/2003.08934)

## Summary
- A NERF is a neural network that can construct a new 3D scenes, trained from a set of 2D photos
- Neural networks as a new way of storing 3D data 
- Super efficient in space 
    - Weights of the network more compact than voxels or other representations
    - In example, only 5MB for network weights, which is less memory than input images (!)
    - Not time tho: Takes 1-2 days to optimize a scene on one GPU
- Use cases: AR, assets, ablations?
    - Imagine in a game, instead of having a bunch of meshes, or voxels, now you have a neural network that you query for a given view to render

## How does it work?
- One MLP that's overfit to one scene (ex. 30 images of a tree) outputs color and density 
    - Very different from classic deep learning where you would have a bunch of different scenes to train on
    - One network that's not useful to other applications (ex. just renders this tree)

### Input 
The neural network gets 2 inputs:
1. Position `x`: a 3D vector (x, y, z)
2. Viewing direction `d`: unit vector (θ, ϕ)
Asking: "if I look from here, to this pixel, what am I going to see?"

### Output
1. Color `c`: (r, g, b) (function of both position and direction)
2. Volume density: `σ` (only function of position - a trick for simplicity)
Answering: "nothing bc there's nothing there" or "it's red"

## How does it render a scene?
```
For each pixel in image:
    Shoot a ray, sample along the ray
    Ask the network "Is there something there, and if so, what color?"
    Model shoots a ray and outputs a color
```
### How do we train the NeRF?
- The whole process above is differentiable: if you have an image, you can calculate loss 
- Size of dataset is # of px * # of pictures
- Overfit to the 30 or so images you have
- At the end, the weights represent scene

### Rendering
- Volume rendering (rendering a 2D representation of a sampled 3D dataset) with radiance fields (function that spits out color for a given position and direction)
- The expected color C(r) of camera ray with near and far bounds is:
    - Integral (from near to far bound) of
    - T(t) - the probability that the ray doesn't hit anything (probability of empty space) * color * other things

## Tricks to get this to work
### Positional encoding
- Mapping input data points `xyz0ϕ` to a higher dimensional space to approximate higher frequency
- Allows you to show fine grain details (like a float isn't good enough for this)
- Construct a hierarchy of sine waves 
- Lowest hierarchy is `/––\__/ ` for coarse grain to `/\/\/\` for fine grained 
- This gives network a choice of which scale (detailed or not) it wants for a position

### Hierarchical volume sampling
- Instead of one network, we have two networks: one coarse and one fine for different levels of detail
- Allows us to optimize where to sample more densely (since sampling everywhere in the scene takes a lot of time)
    - First, evaluate the coarse network, and focus more samples where the coarse network decides is important

#### Questions to look up later
- How far are we from being able to do this in real time? Will this take over current methods in games eventually? 
- Are there any downsides to only generating for one image without outside knowledge? For example, if I want to render my dog, and I take 30 pics mostly from the front, but want a back photo, it prob won't do well. But if it was trained on more dogs, it would do better
- How do they deal with the different coordinate spaces? like 2d to 3d and then back or does it stay in 2?
- What are transformers? Attention? 25:31
- How does the training work? It says it overfits but how?

# Jon Barron - Understanding and Extending Neural Radiance Fields
Implicit representation: Point clouds? continuous

