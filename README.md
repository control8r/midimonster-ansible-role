MIDIMonster Ansible role
========================

This Ansible role has the goal to install a functional MIDIMonster instance on a system of your choice, running debian.
There is also the possibility to set up a service via systemd.

Currently, only Debian bullseye is supported.
Contributions to get more systems compatible are welcome.

ToDo
----
- Add configuration deployment
  - only_update_config mode. / Without rebuilding.


Role Variables
--------------

|             Variable            |  Example Value  |           Default Value          |                Description               |
|:-------------------------------:|:---------------:|:--------------------------------:|:----------------------------------------:|
|       midimonster_version       |       v0.6      |              master              |         The MIDIMonster version.         |
|      midimonster_build_root     | /tmp/mybuilddir |         /tmp/midimonster         |     Temporary directory for building.    |
|        midimonster_prefix       |        -        |               /usr               |       Install prefix for binaries.       |
|       midimonster_plugins       |        -        |         /lib/midimonster         | Install path for backend shared objects. |
|     midimonster_default_cfg     |        -        | /etc/midimonster/midimonster.cfg |        Default configuration file.       |
|     midimonster_example_cfg     |        -        |        /share/midimonster        | Install path for example configurations. |
| midimonster_create_systemd_unit |        -        |               true               |           Create systemd unit.           |

Example Playbook with default variables
---------------------------------------

    - name: Default MIDIMonster deployment.
      gather_facts: false
      hosts: all
      roles:
        - midimonster

Example Playbook with customizations
------------------------------------

    - name: Default MIDIMonster deployment.
      gather_facts: false
      hosts: all
      tasks:
    
        - name: midimonster-deployment
          include_role:
            name: midimonster
          vars:
            - midimonster_version: "master" #Default: "master"
            - midimonster_build_root: "/tmp/midimonster" #Default: "/tmp/midimonster"
            - midimonster_prefix: "/usr" #Default: "usr"
            - midimonster_plugins: "/lib/midimonster" #Default: "/lib/midimonster"
            - midimonster_default_cfg: "/etc/midimonster/midimonster.cfg" #Default: "/etc/midimonster/midimonster.cfg"
            - midimonster_example_cfg: "/share/midimonster" #Default: "/share/midimonster"
            - midimonster_create_systemd_unit: true #Default: true

License
-------

BSD-2-Clause

Author Information
------------------

Written by Spacelord09 / Leon Meier.
