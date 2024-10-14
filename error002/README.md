# Solving "Reduce the Size of Images in Persistent Storage (/var/lib/containerd) by Setting discard_unpacked_layers to True"

## Description

This guide provides steps to address the warning or error message regarding the need to reduce the size of images in persistent storage by enabling the discard_unpacked_layers feature in Containerd. This configuration can help optimize disk space by removing unused layers from container images.

## Understanding the Issue

The error message indicates that the current configuration of Containerd may be leading to inefficient storage usage, particularly in the /var/lib/containerd directory. By enabling discard_unpacked_layers, Containerd can reclaim disk space by discarding layers that are no longer in use.

## Steps :-

### Edit the Configuration File

Open the configuration file in a text editor:

```bash
sudo vi /etc/containerd/config.toml
```

Look for the plugins section, specifically the io.containerd.grpc.v1.cri configuration block. If it does not exist, you can add it.

Add or modify the discard_unpacked_layers setting as follows:

```bash
[plugins."io.containerd.grpc.v1.cri"]
  ...
  discard_unpacked_layers = true
```

Ensure this line is included under the appropriate section.

### Restart Containerd

After saving the changes to the configuration file, restart the Containerd service for the changes to take effect:

```bash
sudo systemctl restart containerd
```

### Verify Configuration

To verify that the configuration has been applied correctly, you can check the status of Containerd and ensure there are no errors:

```bash
sudo systemctl status containerd
```

### Clean Up Unused Images and Layers

After enabling the discard_unpacked_layers option, it may still be necessary to manually clean up unused images and layers to free up disk space. You can do this using the following command:

```bash
sudo nerdctl -n k8s.io images prune -a
```

This command will remove dangling and unused images from your Containerd environment.

## Final Note

If you find this repository useful for learning, please give it a star on GitHub. Thank you!

**Authored by:** [ELemenoppee](https://github.com/ELemenoppee)