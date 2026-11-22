# DIF-SLAM

This is the official public project page for **DIF-SLAM**, a depth-informed
extension of the AQUA-SLAM visual--DVL--inertial underwater localization
framework.

## Overview

DIF-SLAM adds a synchronized depth prior to the local DVL--IMU optimization
pipeline. The prior constrains the configured depth direction in the map
frame, while stereo visual observations provide image geometry and DVL--gyro
preintegration provides short-term motion information. The system is designed
for underwater environments where visual tracking can become weak or
intermittent.

## Public source snapshot

The public snapshot in [`code/core/`](code/core/) includes:

- stereo frame construction and visual tracking;
- DVL--gyro preintegration;
- pose optimization and depth-prior edges;
- keyframe-level DVL--IMU bundle adjustment and adaptive depth-factor weighting;
- local mapping, keyframe, map, and optimization types.

This is a source snapshot for inspection and research reference. It does not
include datasets, ROS bags, trajectories, evaluation results, binaries,
build directories, vocabulary files, or private experiment scripts, and it is
not guaranteed to build as a standalone repository. The original integration
also requires the corresponding AQUA-SLAM/ORB-SLAM3 dependencies, g2o, sensor
calibration, and runtime configuration.

The adaptive depth-factor weighting described in the manuscript is implemented
in keyframe-level local bundle adjustment in
[`DvlGyroOptimizer.cpp`](code/core/src/DvlGyroOptimizer.cpp). This code adjusts
the depth-factor weight using normalized depth-residual statistics and the
fraction of local keyframes with degraded visual tracking.

A separate frame-level optimizer-switching prototype in
[`Tracking.cc`](code/core/src/Tracking.cc) remains disabled with `#if 0`.
That prototype was not used in the reported experiments.

## Repository layout

- `code/`: source code and code-specific documentation.
- `datasets/`: reserved for datasets and dataset documentation to be added in
  a future release.

## Availability

The complete experiment configurations, evaluation tools, and UVDA-Sim dataset
will be released upon acceptance of the paper.

## Attribution

DIF-SLAM is developed on top of AQUA-SLAM and ORB-SLAM3. The selected source
files retain their upstream copyright and license notices. Please follow the
licenses of all upstream components when using this repository.

## Citation

A citation entry will be provided together with the research release.

## Contact

For questions about this project, please open an issue.
