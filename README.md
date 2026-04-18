# VisualLOD: A visual-driven LOD framework for continuous visualization of realistic 3D building scenes
VisualLOD is a visual-driven LOD framework for continuous visualization of realistic 3D building scenes. It can generates LODs with more consistent geometric-texture fidelity and more balanced cross-level fidelity variations, ensures that visual artifacts caused by level transitions remain below the threshold of human visual resolution, thereby facilitating smoother LOD visualization. It can quickly reduce model complexity to adapt to 3D visualization requirements of different performance scenarios (e.g., games, digital twins, virtual reality).


## 1 Core Features
### 1.1 Texture Optimization
- Automatically optimize model's texture layout. Charts from single or multiple textures are packed into a single texture with the optimal resolution while preserving the pixel resolution of the model.

### 1.2 Model Optimization
- Automatically optimize the model's geometric and texture information. Minimize data redundancy while preserving both the degree of fidelity and the geometry-texture matching relationship.

#### Fig. 1 The results of model optimization.
<img width="885" height="684" alt="image" src="https://github.com/user-attachments/assets/3d8d6dd2-de71-42f2-9014-b0e9aebf7792" />

### 1.3 LOD Construction
- Generate multi-level LOD models on demand, supporting custom LOD level counts. Model is optimized and simplified at multiple levels to construct its LODs with a balanced cross-level decreasing fidelity.

#### Fig. 2 The results of LOD construction.
<img width="885" height="457" alt="image" src="https://github.com/user-attachments/assets/4ef008cd-b290-4f43-8452-fe4421ac67fd" />

### 1.4 Continuous LOD visualization
- During visualization, the LODs are dynamically selected and rendered according to the viewpoint state，and the rendering results before and after LOD switching are almost identical in visual effects.

#### Fig. 3 Comparison of the visualization effects before and after LOD switching.
<img width="885" height="1057" alt="image" src="https://github.com/user-attachments/assets/89114233-bfe6-4201-b2fa-b3e47c830fdf" />


## 2 Multiple Running Modes
The tool provides three flexible running modes, allowing you to execute only the specified optimization phase as needed:
| Mode | Description |
|------|-------------|
| `TextureOptimization` | Execute texture optimization (repacking), output textures with higher utilization rates |
| `ModelOptimization` | Execute model optimization, including texture optimization and geometry optimization |
| `LOD` | Build LOD with custom levels, generate the specified number of LOD levels on demand |


## 3 Command-Line Usage
### 3.1 Texture Optimization Mode
```bash
./VisualLOD.exe TextureOptimization -i Data/ModelName.obj -o Output/ModelName/
```

### 3.2 Model Optimization Mode
```bash
./VisualLOD.exe ModelOptimization -i Data/ModelName.obj -o Output/ModelName/
```

### 3.3 Custom LOD Construction Mode
```bash
./VisualLOD.exe LOD -i Data/ModelName.obj -o Output/ModelName/ -level n
```

### 3.4 Parameter Description
| Parameter | Description |
|-----------|-------------|
| Running Mode (1st parameter) | Optional values: `TextureOptimization`/`ModelOptimization`/`LOD` |
| `-i` | Input 3D model path (.obj format) |
| `-o` | Output directory path (save path for optimized models/textures) |
| `-level` | LOD level count (required only for LOD mode, positive integer) |


## 4 Example
As the viewpoint state continuously changes, the LODs are dynamically selected and rendered. The visual discrepancies caused by the differences between LODs are beyond the resolution capability of the human eye, ensuring good visual continuity during LOD transitions. 

**Case 1: LOD continuous visualization of individual building**

https://github.com/user-attachments/assets/80493850-75de-4aff-a83e-ed0e5f889df8

**Case 2: LOD continuous visualization of building scenes**

https://github.com/user-attachments/assets/e626dccd-b899-4234-8078-a96f44c24ad5


## 5 Application Scenarios
- Game Development: Generate adaptive LOD models for different performance devices to improve running frame rate;
- Digital Twin/Smart City: Reduce resource usage of models in large-scale scenes and optimize rendering efficiency;
- 3D Visualization Toolchain: Integrate into automated pipelines to batch process model lightweighting.


## 6 Notes
1. Only .obj format 3D models are supported currently;
2. The output directory needs to be created in advance, the tool does not automatically create non-existent directories temporarily;
3. The dependent geometry/image operation libraries need to be implemented or integrated by yourself (interface calls in the code, need to adapt to actual projects).


## 7 Contribution
Welcome to submit Issues to report problems, propose feature suggestions, or participate in code optimization via Pull Requests.


## 8 License
This project is open source under the [MIT License](LICENSE), free to use, modify and distribute.
