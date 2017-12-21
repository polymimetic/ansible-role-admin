# Ansible Role: Admin

[![Build Status](https://img.shields.io/travis/polymimetic/ansible-role-admin.svg?style=flat-square)](https://travis-ci.org/polymimetic/ansible-role-admin)
[![Release](https://img.shields.io/github/tag/polymimetic/ansible-role-admin.svg?style=flat-square)](https://github.com/polymimetic/ansible-role-admin/releases)
[![License: MIT](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-polymimetic.admin-blue.svg?style=flat-square)](https://galaxy.ansible.com/polymimetic/admin/)

Creates and configures the main user account.

## Requirements

No requirements.

## Dependencies

No dependencies.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    admin_user: "{{ ansible_env.USER }}"

Default admin user.

    admin_home: "{{ ansible_env.HOME }}"

Default admin home.

    admin_fullname: "{{ ansible_user_gecos.split(',')[0] }}"

Default admin full name.

    admin_group: "{{ ansible_env.USER }}"

Default admin user group.

    admin_default_groups:
      - adm
      - sudo
      - cdrom
      - dip
      - plugdev
      - lpadmin

Default groups for the admin user.

    admin_custom_groups: []

Custom groups to add to the admin user.

    admin_groups: "{{ admin_default_groups + admin_group + admin_custom_groups }}"

Secondary groups for the admin user.

    admin_shell: bash

Default admin users shell. Possible values include `bash` or `zsh`.

    admin_xdg_directories:
      - { name: DESKTOP,     path: "$HOME/Desktop",   dir: Desktop,   state: directory }
      - { name: DOWNLOAD,    path: "$HOME/Downloads", dir: Downloads, state: directory }
      - { name: PUBLICSHARE, path: "$HOME/Public",    dir: Public,    state: directory }
      - { name: DOCUMENTS,   path: "$HOME/Documents", dir: Documents, state: directory }
      - { name: TEMPLATES,   path: "$HOME",           dir: Templates, state: absent  }
      - { name: MUSIC,       path: "$HOME",           dir: Music,     state: absent  }
      - { name: PICTURES,    path: "$HOME",           dir: Pictures,  state: absent  }
      - { name: VIDEOS,      path: "$HOME",           dir: Videos,    state: absent  }

XDG user directories. To remove a folder, set its value to "$HOME".

## Example Playbook

To run the role, include it as follows:

    - hosts: all
      roles:
         - { role: polymimetic.admin, x: 42 }

## Credits

This role takes inspiration from the following Ansible roles:

- [cchurch.admin-users](https://github.com/cchurch/ansible-role-admin-users)
- [sansible.users_and_groups](https://github.com/sansible/users_and_groups)
- [franklinkim.users](https://github.com/weareinteractive/ansible-users)
- [singleplatform-eng.users](https://github.com/singleplatform-eng/ansible-users)
- [AsavarTzeth.users](https://github.com/AsavarTzeth/ansible-role-users)
- [opichon.add-user](https://github.com/opichon/ansible-add-user)
- [andyceo.users](https://github.com/andyceo/ansible-role-users)
- [ANXS.generic-users](https://github.com/ANXS/generic-users)
- [SimpliField.users](https://github.com/SimpliField/ansible-users)
- [rickapichairuk.add-admin-user](https://github.com/rickapichairuk/ansible-add-admin-user)
- [ergonlogic.admin-users](https://github.com/ergonlogic/ansible-role-admin-users)
- [manala.accounts](https://github.com/manala/ansible-role-accounts)

## License

This software package is licensed under the [MIT License](https://opensource.org/licenses/MIT). See the [LICENSE](./LICENSE) file for details.

## Author Information

This role was created in 2017 by [Polymimetic](https://github.com/polymimetic).

* ansible-role-admin generated using [ansible-role-skeleton](https://github.com/polymimetic/ansible-role-skeleton)