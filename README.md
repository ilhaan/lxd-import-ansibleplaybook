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
