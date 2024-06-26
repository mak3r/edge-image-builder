# Edge Image Builder Releases

# Next

## General

## API

### Image Definition Changes

### Image Configuration Directory Changes

## Bug Fixes

* [#352](https://github.com/suse-edge/edge-image-builder/issues/352) - Resizing raw images results in dracut-pre-mount failure

---

# v1.0.0-rc3

## API

### Image Definition Changes

* Removed the `operatingSystem/isoConfiguration/unattended` option

## Bug Fixes

* [#319](https://github.com/suse-edge/edge-image-builder/issues/319) - Combustion fails when combustion directory content is larger than half of the RAM of the system
* [#233](https://github.com/suse-edge/edge-image-builder/issues/233) - Use different Helm chart sources for development and production builds
* [#337](https://github.com/suse-edge/edge-image-builder/issues/337) - Re-running raw builds should remove the previous built image
* [#95](https://github.com/suse-edge/edge-image-builder/issues/95)   - Compressed images are not supported
* [#343](https://github.com/suse-edge/edge-image-builder/issues/343) - Embedded Artifact Registry is memory bound
* [#341](https://github.com/suse-edge/edge-image-builder/issues/341) - Make Elemental registry configurable for production builds
* [#258](https://github.com/suse-edge/edge-image-builder/issues/258) - Kubernetes installation doesn't work with DHCP given hostname

---

# v1.0.0-rc2

## General

* Added output at combustion phase to observe the script being executed
* Kubernetes install scripts are now downloaded at runtime instead of during the container image build process
* Bumped Go Version to 1.22
* Added support for using Helm charts from authenticated repositories/registries
* Added support for skipping Helm chart TLS verification and for using Helm charts from plain HTTP repositories/registries
* Added support for providing CA files to Helm resolver for TLS verification
* Added minor formatting improvements to the CLI output

## API

* The `--config-file` argument to the EIB CLI has been renamed to `--definition-file`.
* The `--build-dir` argument to the EIB CLI is now optional and defaults to `<config-dir>/_build`, creating it if it does not exist.
* The `--config-dir` argument to the EIB CLI is now optional and defaults to `/eib` which is the most common mounted container volume.
* New `validate` subcommand is introduced
* The `--validate` argument to the `build` subcommand is now removed

### Image Definition Changes

* Added the ability to configure Helm charts under `kubernetes/helm`

### Image Configuration Directory Changes

* Helm chart values files can be specified under `kubernetes/helm/values`

## Bug Fixes

* [#239](https://github.com/suse-edge/edge-image-builder/issues/239) - Incorrect warning when checking for both .yml and .yaml files
* [#259](https://github.com/suse-edge/edge-image-builder/issues/259) - SCC registration is not cleaned up if RPM resolution fails
* [#260](https://github.com/suse-edge/edge-image-builder/issues/260) - Empty network directory produces a network configuration script
* [#267](https://github.com/suse-edge/edge-image-builder/issues/267) - Embedded registry renders Kubernetes resources even when Kubernetes is not configured
* [#242](https://github.com/suse-edge/edge-image-builder/issues/242) - Empty rpms directory triggers resolution
* [#283](https://github.com/suse-edge/edge-image-builder/issues/283) - Definition file argument to EIB is incorrect
* [#245](https://github.com/suse-edge/edge-image-builder/issues/245) - Pass additional arguments to Helm resolver
* [#307](https://github.com/suse-edge/edge-image-builder/issues/307) - Helm chart parsing logic breaks if "---" is present in the chart's resources
* [#272](https://github.com/suse-edge/edge-image-builder/issues/272) - Custom files should keep their permissions
* [#209](https://github.com/suse-edge/edge-image-builder/issues/209) - Embedded artifact registry starting even when manifests don't have any images
* [#315](https://github.com/suse-edge/edge-image-builder/issues/315) - If Elemental fails to register during Combustion we drop to emergency shell
* [#321](https://github.com/suse-edge/edge-image-builder/issues/321) - Certain Helm charts fail when templated in the `default` namespace
* [#289](https://github.com/suse-edge/edge-image-builder/issues/289) - The services for RPM dependency resolution failed to start

---

# v1.0.0-rc1

## General

* Added support for deploying user-provided Helm charts
* Added support for custom network configuration scripts

## API

### Image Definition Changes

* Removed the `embeddedArtifactRegistry/images/supplyChainKey` attribute
* Changed `operatingSystem/users/sshKey` into `operatingSystem/users/sshKeys` and it is now a list instead of a single string
* Added the ability to configure operating system groups under `operatingSystem/groups`
* Added optional `primaryGroup` field for operating system users
* Added optional `secondaryGroups` field for operating system users
* Added optional `createHomeDir` field for operating system users
* Added optional `uid` field for operating system users

## Bug Fixes

* [#197](https://github.com/suse-edge/edge-image-builder/issues/197) - Consider using ENTRYPOINT instead of CMD
* [#213](https://github.com/suse-edge/edge-image-builder/issues/213) - zypper clean after zypper install
* [#216](https://github.com/suse-edge/edge-image-builder/issues/216) - Update the docs to reflect that systemd can be used for any kind of systemd unit, not just services
