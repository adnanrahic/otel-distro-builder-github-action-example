# OpenTelemetry Distro Builder Github Action Example

This repository demonstrates how to build a custom OpenTelemetry Collector distribution using the [otel-distro-builder](https://github.com/observiq/otel-distro-builder) GitHub Action.

The project includes:

- A manifest file (`manifest.yaml`) that defines the components to include in the distribution
- GitHub Actions workflow (`.github/workflows/multi.yaml`) that builds the collector for multiple platforms
- Bindplane custom collector resource definition for integration with Bindplane

The workflow automatically builds the collector for Linux (amd64/arm64), macOS (arm64), and Windows (amd64) platforms when a version tag is pushed. It creates platform-specific packages (DEB, RPM, APK, ZIP, TAR.GZ) and publishes them as GitHub releases.

This serves as a template for creating your own custom OpenTelemetry Collector distribution with automated multi-platform builds.

## Step-by-step

Add the custom collector resource to Bindplane.

```bash
bindplane apply ./bindplane/custom-collector-resource.yaml
bindplane get agent-type

[output]
opentelemetry-distro-builder-demo	OpenTelemetry Distro Builder Demo (Adnan's fork)	           	https://github.com/adnanrahic/otel-distro-builder-github-action-example	
```

Sync the built collection versions to Bindplane.

```bash
bindplane sync agent-version --agent-type opentelemetry-distro-builder-demo --all
```
