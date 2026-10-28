# Core file manifest

The files in this directory were selected because they contain the algorithmic
path that distinguishes DIF-SLAM from the upstream visual--DVL system.

| Area | Files |
|---|---|
| Tracking and frames | `Tracking.*`, `Frame.*` |
| Depth and pose optimization | `Optimizer.*`, `DvlGyroOptimizer.*`, `G2oTypes.*`, `OptimizableTypes.*` |
| Sensor preintegration | `DVLGroPreIntegration.*`, `ImuTypes.*` |
| Local map and state | `LocalMapping.*`, `KeyFrame.*`, `Map.*`, `MapPoint.*`, `Atlas.*` |
| Existing visual interface | `ORBextractor.*`, `ORBmatcher.*`, `System.*` |
