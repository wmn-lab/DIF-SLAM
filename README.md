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

The research-critical implementation is available in [`code/core/`](code/core/):

- stereo frame construction and visual tracking;
- DVL--gyro preintegration;
- pose optimization and depth-prior edges;
- keyframe-level DVL--IMU bundle adjustment;
- local mapping, keyframe, map, and optimization types.

This is a source snapshot for inspection and research reference. It does not
include datasets, ROS bags, trajectories, evaluation results, binaries,
build directories, vocabulary files, or private experiment scripts, and it is
not guaranteed to build as a standalone repository. The original integration
also requires the corresponding AQUA-SLAM/ORB-SLAM3 dependencies, g2o, sensor
calibration, and runtime configuration.

The adaptive visual-quality-aware branch retained in `code/core/src/Tracking.cc`
is disabled with `#if 0`; it records a future design and was not used for the
reported experiments.

## Repository layout

- `code/`: source code and code-specific documentation.
- `datasets/`: reserved for datasets and dataset documentation to be added in
  a future release.

## Availability

The manuscript describing this work is currently under review. Additional
configuration files, evaluation tools, and supplementary materials will be
released after the paper is accepted for publication.

## Attribution

DIF-SLAM is developed on top of AQUA-SLAM and ORB-SLAM3. The selected source
files retain their upstream copyright and license notices. Please follow the
licenses of all upstream components when using this repository.

## Citation

A citation entry will be provided together with the research release.

## Contact

For questions about this project, please open an issue.
