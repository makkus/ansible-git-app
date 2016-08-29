ansible-git-app
=========

A role to install applications from git, add a init script and ensure it's running.

Role Variables
--------------

````---
# defaults file for ansible-git-app

# the name of the app
git_app_name: dummy-git-app
# the username to own and run the app
git_app_user_name: makkus
# the id of the user to own and run the app
git_app_user_id: 4999
# the groupname to own and run the app
git_app_group_name: makkus
# the id of the group to own and run the app
git_app_group_id: 4999
# the home directory of the user
git_app_user_home: "/home/{{ git_app_user_name }}"
# the git clone uri
git_app_clone_uri: 'https://github.com/makkus/dummy-git-app.git'
# the folder where the configuration of the app is stored (optional)
# will be created and chown'ed to user if it doesn't exist
git_app_conf_path: "{{ git_app_user_home }}/.dummy_app"
# the path where to checkout the code
git_app_code_path: "/opt/{{ git_app_name }}"
# the executable to run, relative to git_app_code_path
git_app_exec_path: "print_time.sh"
# arguments, if any
# git_app_exec_arguments:

# package names of dependencies to be installed
git_app_dependencies: []

git_app_service_type: "simple"

# misc TODO
git_app_systemd_after: "network.target"
git_app_systemd_wantedby: "multi-user.target"
````


Example Playbook
----------------

```---
- hosts: test
  remote_user: root

  vars:
    - git_app_service_type: "simple"

  roles:
    - ansible-git-app
```

License
-------

BSD
