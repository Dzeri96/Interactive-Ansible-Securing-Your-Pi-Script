# Interactive Ansible "Securing Your Raspberry Pi" Script
An Ansible script package designed according to the official ["Securing your Raspberry Pi" guide](https://www.raspberrypi.org/documentation/configuration/security.md).
Made to be as idempotent as possible and includes an interactive setup script.

## Getting Started

### Prerequisites

Ansible is needed run these scripts. If you are unfamiliar with it, google "install Ansible on" Windows/OSX/Ubuntu/Arch...

Configuring the inventory file `/etc/ansible/hosts` with local IP addresses of your Pis is necessary.
It should look like this:
```
[pis]
192.168.0.5
192.168.0.13
```
*This step might be automated in the future with an nmap script.*
### Setup

Before running the main `setup.yml` script, a `vars.yml` file has to be created either by running the interactive setup with 


```
ansible-playbook init.yml
```

or building the file manually, which has the following structure:

```
---
user: AzureDiamond
password: hunter2
strict_security: no             #Refers to disabling PAM/Password logins
default_user_present: True      #True if the pi user is still enabled (default for new Pis)
```

By default this file is in plain text. If you want extra security, run

```
ansible-vault encrypt vars.yml
```
after this, make sure to add the `--ask-vault-pass` flag when running `setup.yml`

### Running the script

Finally, run the script by typing 

```
ansible-playbook setup.yml
```
**Enjoy your set-up Pi!**


## Contributing

Contributions are welcome! Open an issue or go straight for the PR.

## Authors

* **Dzeri96** - *Initial work*

## License

This project is licensed under the MIT License

## Acknowledgments

* As far as I know, ansible does not support writing to encrypted files, having encryption by default is not possible.

