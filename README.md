# lxd-import-ansibleplaybook

This [Ansible Playbook](https://docs.ansible.com/ansible/2.7/user_guide/playbooks.html) looks for [LXD](https://linuxcontainers.org/) image tar files in a directory and imports them to the local image store for public access. Imported image tar files are then moved to a different directory. You can read more about LXD image management and running a public LXD server [here](https://stgraber.org/2016/03/30/lxd-2-0-image-management-512/).

## Instructions
Before running this playbook, the following variables need to be specified in the `external_vars.yml` file: 

* `imagedir`: This is the directory the playbook should look for LXD image tar files. The playbook assumes all `*.tar.gz` files in this directory are LXD images. 
* `lxcpath`: Path to your lxc installation. You can determine this using `which lxc` on Ubuntu. This varies based on installation method. 
* `oldimagepath`: Directory where imported images will be moved to. 

After the variables above have been set, run the playbook using: 
```
ansible-playbook lxd_image_import.yml
```

## Notes
Please note the following: 
* This playbook has only been tested on Ubuntu 16.04 & Ubuntu 18.04 with Ansible 2,7 installed using `pip install ansible`. 
* Currently, there is no error checking in the [LXD image import step](https://github.com/ilhaan/lxd-import-ansibleplaybook/blob/6ff23d321d6d53550fec5bc29677b54f569ef068/lxd_image_import.yml#L14). If an error occurs when multiple image tar files exist in `imagedir`, some images may not be imported as the playbook will halt execution. 
