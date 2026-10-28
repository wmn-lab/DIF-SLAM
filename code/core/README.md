# DIF-SLAM Core Snapshot

This directory contains the research-critical C++ source extracted from the
DIF-SLAM development workspace. It is intended to make the main algorithmic
changes inspectable; it is not a standalone build tree.

## Main modules

- `Tracking.*`: stereo tracking, DVL--gyro motion propagation, local-map
  tracking, and the reserved visual-quality-aware tracking branch.
- `Frame.*`: left/right stereo frame construction, ORB feature extraction,
  stereo matching, depth observations, and frame-level sensor state.
- `Optimizer.*`: pose optimization and depth-prior edge construction.
- `DvlGyroOptimizer.*`: keyframe-level DVL--IMU bundle adjustment with the
  depth-direction prior.
- `DVLGroPreIntegration.*` and `Integrator.*`: DVL and gyroscope
  preintegration and sensor integration state.
- `LocalMapping.*`: local-map processing and invocation of the coupled
  DVL--IMU--depth optimization.
- `KeyFrame.*`, `Map.*`, `MapPoint.*`, and `Atlas.*`: map and keyframe state
  used by the coupled optimization.
- `G2oTypes.*`, `OptimizableTypes.*`, and `ImuTypes.*`: optimization vertices,
  edges, and sensor types.

## Current implementation path

The reported DIF-SLAM experiments use visual local-map pose optimization in
the tracking thread. The depth prior is passed to the keyframe-level local
DVL--IMU bundle adjustment and constrains the configured map-frame axis.
DVL and gyroscope measurements also provide motion propagation when visual
tracking fails.

The `#if 0` branch in `Tracking.cc` records a proposed visual-quality-aware
tracking design. It is intentionally disabled and was not used to generate
the reported experimental results.

## Scope of this snapshot

This public snapshot intentionally excludes datasets, ROS bags, trajectories,
evaluation outputs, binaries, build directories, ORB vocabulary files, and
private experiment scripts. Camera calibration, topic names, depth-axis
calibration, and sensor extrinsics must be supplied through the configuration
used by the original AQUA-SLAM integration.

The selected files retain upstream ORB-SLAM3/AQUA-SLAM licensing and
copyright notices. Please follow the licenses of the upstream components
when redistributing or building this code.
