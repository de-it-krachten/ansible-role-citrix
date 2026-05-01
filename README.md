[![CI](https://github.com/de-it-krachten/ansible-role-citrix/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-citrix/actions?query=workflow%3ACI)


# ansible-role-citrix

Installs Citrix Workspace App on a variety of Linux distributions.<br>

- Download the required packages from [link](https://www.citrix.com/downloads/workspace-app/linux/workspace-app-for-linux-latest.html).<br>
- Put the packages in a custom directory on the Ansible control node.<br>
- Set variable `citrix_package_path` to the package location.<br>



## Dependencies

#### Roles
None

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- Red Hat Enterprise Linux 10<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- RockyLinux 10
- OracleLinux 8
- OracleLinux 9
- OracleLinux 10
- AlmaLinux 8
- AlmaLinux 9
- AlmaLinux 10
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Debian 13 (Trixie)
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Ubuntu 26.04 LTS
- Fedora 42
- Fedora 43

Note:
<sup>1</sup> : no automated testing is performed on these platforms


## Role Variables
### defaults/main.yml
<pre><code>
# Citrix Workspace App version
citrix_version: "26.01.0.150"

# Define location that holds the packages
citrix_package_path: files

# Install USB support
citrix_usb_support: false
</pre></code>

### defaults/family-Debian.yml
<pre><code>
# Main package name
citrix_package_filename: "icaclient_{{ citrix_version }}_amd64.deb"

# USB support package
citrix_usb_package_filename: "ctxusb_{{ citrix_version }}_amd64.deb"
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
# Main package name
citrix_package_filename: "ICAClient-rhel-{{ citrix_version }}-1.x86_64.rpm"

# USB package name
citrix_usb_package_filename: "ctxusb-{{ citrix_version }}-1.x86_64.rpm"
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'citrix'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'citrix'
      ansible.builtin.include_role:
        name: citrix
</pre></code>
