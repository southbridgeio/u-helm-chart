# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.7] - 2026-03-12

### Added
- ConfigMap annotations support

## [0.2.6] - 2026-03-12

### Added
- Support for Gateway API `HTTPRoute` via new `route` configuration block
- New template `templates/route.yaml` with backend bound to chart-managed Service (`application.fullname` + `service.port`)
- Test values scenario for Gateway API route rendering (`tests/values-test-route.yaml`)

### Changed
- Updated documentation for Gateway API route usage and values
- Route template now renders only when deployment is enabled to avoid referencing a non-existent chart-managed Service

## [0.2.5] - 2026-01-14

### Added
- Support for `shareProcessNamespace` parameter to enable process namespace sharing between containers in the pod

## [0.2.4] - 2025-12-03

### Added
- Support for PersistentVolumeClaims (PVC) via `persistentVolumeClaims` parameter
- Automatic volume and volumeMount configuration for PVCs in main container
- Individual PVC support for init containers via `pvc.enabled: true` in `initContainers.containers[].pvc`
- Individual PVC support for sidecar containers via `pvc.enabled: true` in `extraContainers.containers[].pvc`
- PVC template created before deployment to ensure proper resource ordering

### Changed
- Renumbered template files to maintain logical order (PVC template is now 4_pvc.yaml, placed before deployment)
- PVCs from `persistentVolumeClaims` are now mounted only in the main container (not automatically in init/sidecar containers)
- Init containers and sidecar containers require individual `pvc` configuration if persistent storage is needed

## [0.2.3] - 2025-11-28

### Added
- Support for init containers via `initContainers` parameter for pre-startup initialization tasks (database migrations, file downloads, etc.)

## [0.2.2] - 2025-11-19

### Added
- Support for custom container name via `containerName` parameter (defaults to Chart.Name if not set)
- Support for custom command in main container via `command` parameter

## [0.2.1] - 2025-11-13

### Added
- Support for plain environment variables (not only from secrets) via `env` parameter
- Automatic Helm hooks for `ExternalSecret` resources in `extraManifests` to ensure they are created before deployment
- Support for plain environment variables in Job, CronJob, and sidecar containers
- Comprehensive test suite with 12 test scenarios covering all features

### Changed
- Updated documentation to reflect new environment variables functionality
- Improved `extraManifests` template to automatically add pre-install/pre-upgrade hooks for ExternalSecret resources

### Fixed
- Fixed issue where deployment could fail with `ConfigContainerError` when using ExternalSecret resources

## [0.2.0] - 2025-11-13

### Added
- Support for disabling deployment via `deploymentDisable` parameter
- Plain Ingress feature with automatic service creation
- Enhanced ingress configuration options
- Support for multiple ingress resources

### Changed
- Chart version updated to 0.2.0
- Improved ingress template structure

## [0.1.9] - Previous

### Added
- Initial chart release
- Basic deployment, service, and ingress support
- Job and CronJob support
- ConfigMap and volume management
- Sidecar containers support
- Autoscaling (HPA) support
- Environment variables from secrets
- Extra manifests support

---

[0.2.6]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.6
[0.2.5]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.5
[0.2.4]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.4
[0.2.3]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.3
[0.2.2]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.2
[0.2.1]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.1
[0.2.0]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.2.0
[0.1.9]: https://github.com/chaser100/u-helm-chart/releases/tag/v0.1.9
