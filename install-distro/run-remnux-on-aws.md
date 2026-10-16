# Run REMnux on AWS

To run REMnux on Amazon EC2, launch one of the REMnux Amazon Machine Images (AMIs). Each AMI has REMnux installed in cloud mode, which keeps SSH on.

## Choose the AMI <a href="#choose-ami" id="choose-ami"></a>

The AMIs are in the us-east-1 region (N. Virginia), and their owner is AWS account `726701726204`. Choose the one that matches the processor of your instance type.

| Processor | AMI ID |
|-----------|--------|
| Intel or AMD (amd64) | `ami-0b8b5c94f1b7cf77a` |
| Graviton (arm64) | `ami-07ba88112d5032efd` |

<a href="https://console.aws.amazon.com/ec2/home?region=us-east-1#LaunchInstances:ami=ami-0b8b5c94f1b7cf77a" class="button secondary">Launch the amd64 AMI</a> <a href="https://console.aws.amazon.com/ec2/home?region=us-east-1#LaunchInstances:ami=ami-07ba88112d5032efd" class="button secondary">Launch the arm64 AMI</a>

The arm64 AMI lacks the tools that REMnux supports only on amd64. They include Wine and the tools that depend on it, such as scdbg, plus the tools [listed for the container](remnux-as-a-container.md#tools-unavailable-on-arm-systems).

Choose an instance type with at least 4 GB of memory, such as `t3.medium`, instead of the launch page's default. The root volume starts at 64 GiB. Enlarge it at launch if you'll need more room for samples.

## Connect to REMnux <a href="#connect" id="connect"></a>

Sign in over SSH as `remnux`, using the key pair you chose at launch. The EC2 console may list the username as root, but REMnux uses `remnux`:

```
ssh -i YOUR_KEY.pem remnux@YOUR_INSTANCE_IP
```

SSH accepts only your key pair, and it refuses logins as root. The `remnux` account's password is locked, so the `malware` password of the virtual appliance doesn't work here. You can still run commands as root with `sudo`, which doesn't ask for a password.

To reach the REMnux desktop, follow the [GUI interactions in the cloud](../tips/remnux-config-tips.md#gui-cloud-remnux) tips. For VNC, you set a separate password with `vncpasswd`, as those tips describe. If another tool needs a password for the `remnux` account, set a strong one with `sudo passwd remnux`. SSH keeps refusing password logins either way.

## Keep REMnux Up to Date <a href="#update" id="update"></a>

Right after you first connect, and once in a while after that, update REMnux by running this command as `remnux`:

```
remnux install
```

The installer reuses the AMI's cloud mode, which keeps SSH on. Don't add `--mode=dedicated`, because the installer then turns off SSH and you'd lose access to the instance.
