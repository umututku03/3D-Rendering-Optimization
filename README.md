

# Cube Rendering and Camera Optimization

This project involves rendering a 3D cube, projecting its vertices onto 2D images, and optimizing the camera parameters to minimize the error between the projected points and ground truth 2D points using gradient descent. The project uses PyTorch for optimization and rendering.

## Project Structure

- `main.py`: The main script that performs rendering and optimization.
- `extrinsics/`: Directory containing the saved camera extrinsic matrices from the NumPy rendering process.
- `computed_2d_points/`: Directory containing the saved 2D points from the NumPy rendering process.
- `renders_pillow/`: Directory where rendered images are saved.
- `optimized_params.pth`: File containing the optimized camera parameters.

## Dependencies

- `numpy`
- `Pillow`
- `torch`
- `matplotlib`

## Usage

1. **Prepare the Environment:**

   Ensure you have the required dependencies installed. You can install them using pip:

   ```bash
   pip install numpy pillow torch matplotlib
   ```

2. **Run the Optimization:**

   Execute the `main.py` script to perform the rendering and optimization process.

   ```bash
   python main.py
   ```

3. **Inspect the Results:**

   The optimized camera parameters will be saved in the `optimized_params.pth` file. Rendered images and corresponding 2D points will be saved in their respective directories.

## Explanation of the Code

### Rendering Process

1. **Define Cube Vertices and Edges:**

   The vertices and edges of the cube are defined in the `cube_vertices` and `cube_edges` arrays.

2. **Camera Setup:**

   Initial camera setup, including the target position and up vector, is defined. The projection matrix is also set up to simulate a perspective projection.

3. **Rendering Loop:**

   The camera is rotated around the cube, and for each position, the cube's vertices are projected onto a 2D image. The projected points are saved for later comparison.

### Optimization Process

1. **Load Ground Truth Data:**

   The saved 2D points and camera extrinsics from the previous NumPy rendering process are loaded.

2. **Define Model and Loss Function:**

   A simple neural network model (`LookAt`) is defined to compute the camera's view matrix. The `ProjectVertex` class is used to project the 3D vertices onto 2D points. The mean squared error (MSE) loss function is used to measure the difference between the projected points and ground truth 2D points.

3. **Gradient Descent Optimization:**

   The camera parameters are optimized using gradient descent to minimize the error between the projected points and the ground truth 2D points.

4. **Save Optimized Parameters:**

   The optimized camera parameters are saved to the `optimized_params.pth` file.

5. **Validation and Visualization:**

   After optimization, the errors between the projected points and ground truth 2D points are computed and visualized.

## Future Work

- Improve the rendering quality by adding lighting and shading effects.
- Extend the optimization to include more complex camera models.
- Experiment with different optimization algorithms and loss functions.
