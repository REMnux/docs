# Install with Distrobox

{% hint style="info" %}
This REMnux Distrobox container is community-maintained and not officially supported by the REMnux project team. While efforts are made to ensure compatibility, updates to REMnux may occasionally cause issues.
{% endhint %}

## Quick Start

### Prerequisites
- Docker or Podman
- Distrobox installed ([Installation Guide](https://github.com/89luca89/distrobox#installation))

### Installation

1. Create the REMnux container:

```bash
distrobox create --name REMnux --image marcelalexandrunitan/remnux-distrobox:latest
```

2. Enter the container:

```bash
distrobox enter REMnux -- bash -l
```

> **Note**: The `-- bash -l` parameter is required during the first launch if your default shell is not bash (e.g., zsh). This ensures REMnux's `update`/`upgrade` commands function correctly. After initial setup, you can simply use `distrobox enter REMnux`.
### Keeping REMnux Updated

Run this command from inside the container to update all REMnux components:

```bash
remnux upgrade --mode=addon --user=$(whoami)
```

## Configuration Details

### Kernel Headers

The container automatically creates a placeholder kernel-headers package matching your host kernel version and marks it as "held" to prevent update failures. This ensures REMnux's CLI tools won't attempt to install incompatible kernel headers from Ubuntu 20.04 repositories.

### User Files

A default `remnux` user is preconfigured with analysis-ready settings. Important config files are located at:

- `/home/remnux/.config/Code/User/settings.json` - VSCode settings
- `/home/remnux/.ghidra/` - Ghidra configuration and data types
- `/home/remnux/.malwapi.conf` - Malware API configuration

Copy specific configuration files to your user's home directory
