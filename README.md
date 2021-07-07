Role Name
=========

Ansible Role to clean Linux instances with Resin webserver and free disk space.

Requirements
------------

- Ansible 2.6
- Linux operative system
- Resin (in VM instance)

Role Variables
--------------

```
#log-files
cri_log_files_remove_enabled: yes

cri_log_files_paths: "/var/log/resin"
cri_log_files_patterns: "*"
cri_log_files_age: 90d
cri_log_files_recurse: yes
cri_log_files_hidden: yes
cri_log_files_file_type: "file" # delete files
cri_log_files_follow: no # don't follow symbolic links by default

#temp-files
cri_temp_files_remove_enabled: yes

cri_temp_dump_files_paths: "/var/resin"
cri_temp_dump_files_patterns: "*.hprof"
cri_temp_dump_files_recurse: no
cri_temp_dump_files_hidden: yes
cri_temp_dump_files_file_type: "file"

cri_temp_git_files_paths: "/var/resin/resin-data/default/.git"
cri_temp_git_files_patterns: "*"
cri_temp_git_files_recurse: yes
cri_temp_git_files_hidden: yes
cri_temp_git_files_file_type: "any" # any = delete files, directories and symbolic links
```

Example Playbook
----------------

```
- 
  hosts: tag_intra-crm-webserver
  become: yes # usuario root
  roles:
    - {role: clean-resin-instance, tags: ["clean-resin-instance"]}
```


Author Information
------------------

Augusto Mendoza (amendoza@navent.com)

