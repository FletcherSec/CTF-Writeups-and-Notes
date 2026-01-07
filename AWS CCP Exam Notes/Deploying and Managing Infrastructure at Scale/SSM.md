- AWS Systems Manager
- Helps manage your [[EC2]] and On-Premises systems at scale
- Hybrid AWS service
- Get operational insights about the state of your infrastructure
- Suite of 10+ products
- Most important features are:
	- Patching automation for enhanced compliance
	- Run commands across an entire fleet of servers
	- Store parameter configuration with the SSM parameter Store
- Works for Linux, Windows, MacOS, and Raspberry Pi OS

##### How it works
- We need to install the SSM agent onto the systems we control
- Installed by default on Amazon Linux [[AMI]] and some Ubuntu AMI
- If an instance cant be controlled with SSM, its probably an issue with the SSM agent
- Thanks to the SSM agent, we can run commands, patch and configure our servers