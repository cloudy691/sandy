---
name: dotnet-wpf
description: Build, run, and debug .NET WPF applications. Handles MSBuild commands, project creation, NuGet packages, deployment, and compilation errors.
---

# /dotnet-wpf Command

Build, run, debug, and package .NET WPF applications.

## Build & Run

```
/dotnet-wpf build [project.csproj]
/dotnet-wpf run [project.csproj]
```

Runs `dotnet build` / `dotnet run` with the given project file. Defaults to first .csproj in current directory.

## Create Project

```
/dotnet-wpf init [name] [template]
```

Templates:
- `wpf` — vanilla .NET WPF (default)
- `wpf-mvvm` — .NET WPF with CommunityToolkit.Mvvm
- `wpf-maui` — .NET MAUI for cross-platform Windows/macOS

Example:
- `/dotnet-wpf init MyApp`
- `/dotnet-wpf init MyApp wpf-mvvm`

## Debug

```
/dotnet-wpf debug [issue description]
```

Analyzes build errors, runtime crashes, or XAML parse exceptions.

## Deploy

```
/dotnet-wpf publish [framework]
```

Publishes standalone or framework-dependent executable.
Frameworks: `win-x64` (default), `win-arm64`, `win-x86`, `self-contained`

Example:
- `/dotnet-wpf publish` → self-contained for current OS
- `/dotnet-wpf publish win-x64` → explicit target

## Manage Packages

```
/dotnet-wpf add-package <package-name>
/dotnet-wpf remove-package <package-name>
/dotnet-wpf update-packages
```

Manages NuGet packages for the WPF project.

## Check Version

```
/dotnet-wpf version
```

Shows .NET SDK version, installed workloads, and platform info.
