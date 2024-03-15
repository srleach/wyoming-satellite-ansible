# Automating Wyoming Satellite Deployment

> The driver installer for this playbook was adapted from that found in the official [Wyoming Satellite Repository](https://github.com/rhasspy/wyoming-satellite/blob/962b2f5dc6ed0d8b05671f1ade092407ed6251cd/etc/install-respeaker-drivers.sh) and assumes you're using the seeed or raspiaudio ultra boards based on the WM8960 Chipset.

> The original inspiration for this came from the video produced by FutureProofHomes [on YouTube](https://www.youtube.com/watch?v=kS0agn13hhU) and also documented [here](https://github.com/FutureProofHomes/wyoming-enhancements)


Welcome to the Wyoming Raspberry Pi Setup playbook! 

This Ansible playbook simplifies the installation of Wyoming Satellite and Wyoming OpenWakeWord on your Raspberry Pi(s), 
completing a full deployment from a base image in under 20 minutes. 

Whether you're configuring one device or many, the playbook automates the process for consistency and reliability. 

Please feel free to report issues, and contribute enhancements through pull requests.

## Usage

### Prerequisites & Notes

- Burn one or more SD Cards with Pi imager or similar. 
  - I've tested on the "Raspberry Pi OS (Legacy, 64-bit) Lite" version released `2024-03-12` on a Pi Zero 2 W but it should work elsewhere too. 
  - To use this play, you'll need the username and an authorised key and be able to reach the pi over ssh. More on this later.
- Rename the `hosts.yaml.example` file in the root directory to `hosts.yaml`. For each host:
  - Configure its IP or hostname
  - Configure `ansible_user` and `ansible_ssh_private_key_file` to authenticate against the targets - you'll have set these up when burning your cards.
  - Configure `satellite_name` value to something descriptive for each host. This is the name you'll see in Home Assistant. 
    - It can be changed easily enough by re-running the play with an updated value.
- If you'd like to adjust the wake word used by OpenWakeWord, set it in `group_vars/all.yaml`
- Caution: I opted to use this to up the swapfile size to help speed up the initial run. 
  - This is set in group_vars/all.yaml where you'll also find some more config.

### Running

```
 ansible-playbook -i hosts.yaml playbooks/deploy-wyoming.yaml
```

## Performance

> Your mileage may vary! Image written using Raspberry Pi Imager with cached image.

- SD Card write (3 minutes)
- SD Card veriy (1 minute)
- Pi First Boot (2 minutes)
- Play Finished (17 minutes)
