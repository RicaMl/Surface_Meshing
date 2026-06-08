# Surface Meshing – Exploration & Metrics

This notebook illustrates the generation of triangular meshes of geometric primitives (sphere, cylinder, plane, torus), the calculation of quality metrics (aspect ratio, skewness, angles), and the estimation of discrete Gaussian curvature. It also studies the effect of mesh resolution on curvature accuracy.

## Contents

1. **Primitive generation** with `trimesh`
2. **Quality metrics**: aspect ratio, minimum angle, skewness
3. **Discrete Gaussian curvature** (angular defect method)
4. **Shape signature**: histograms and statistical features
5. **Resolution comparison** on a sphere (curvature convergence)
6. **Visualizations**: 3D meshes, metric distributions, curvature maps, radar chart

## Dependencies

- Python 3.7+
- `trimesh`
- `numpy`
- `scipy`
- `matplotlib`

Quick installation:
```bash
pip install trimesh numpy scipy matplotlib
```

## Usage

Run the notebook cell by cell. The main functions are:

- `triangle_angles(verts, faces)` – interior angles of triangles
- `aspect_ratio(verts, faces)` – ratio of longest to shortest edge
- `skewness(angles_deg)` – deviation from equilateral
- `gaussian_curvature(mesh)` – discrete Gaussian curvature
- `curvature_features(K)` – feature vector (mean, std, flat/positive/negative fractions)

Results are displayed as graphs (histograms, curvature maps, radar, convergence).

## Expected results

- The sphere has high‑quality triangles (aspect ratio near 1, angles ~60°).
- The cylinder has highly elongated triangles (poor aspect ratio).
- Gaussian curvature distinguishes primitives:
  - Sphere: constant K > 0
  - Cylinder: K ≈ 0 on the side
  - Plane: K ≈ 0 everywhere
  - Torus: positive and negative K (outer/inner regions)
- Curvature error on the sphere decreases quadratically with face count.

## Future extensions

- Adaptive meshing (refine based on curvature)
- Segmentation of complex shapes into primitives
- Neural networks (PointNet, GNN) on curvature signatures
