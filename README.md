# Automating Wyoming Satellite Deployment

> The driver installer for this playbook was adapted from that found in the official [Wyoming Satellite Repository](https://github.com/rhasspy/wyoming-satellite/blob/962b2f5dc6ed0d8b05671f1ade092407ed6251cd/etc/install-respeaker-drivers.sh) and assumes you're using the seeed or raspiaudio ultra boards based on the WM8960 Chipset.

> The original inspiration for this came from the video produced by FutureProofHomes [on YouTube](https://www.youtube.com/watch?v=kS0agn13hhU) and also documented [here](https://github.com/FutureProofHomes/wyoming-enhancements)

## Usage

Rename the hosts.yaml.example file in the inventories/ directory to hosts.yaml. This file serves as your inventory, defining your hosts and their associated variables. In hosts.yaml, replace the placeholders (ip_or_hostname, your_user, path_to_key, Name_Of_Satellite, 2048) with the actual values for your satellite hosts. The ansible_user should be the username you use to SSH into your hosts, ansible_ssh_private_key_file should be the path to the SSH private key, satellite_name can be a descriptive name for your satellite, and desired_swap_size specifies the desired swap size for your hosts. 