ansible-haproxy
=========

This role will configure two haproxy nodes in an active-passive configuration on DigitalOcean Droplets. Th

Role Variables
--------------

I recommend setting the *do_token* and *ha_auth_key* variables in **group_vars/*group_name*/vars.yml** and setting them to the values stored in an ansible-vault encrypted file in **group_vars/*group_name*/vault.yml**

```ansible
# DigitalOcean access token
do_token: "{{ vault_do_token }}"

# Generated ha auth key.
ha_auth_key: "{{ vault_ha_auth_key }}"
```

Just don't forget to set *vault_do_token* and *vault_ha_auth_key*.

You can adjust the following two variables in defaults/main.yml

    timezone: "America/Los_Angeles"
    locale: "en_US.UTF-8"

Example usage
----------------

You should install the role before attempting to execute directly from a playbook.

    ansible-galaxy install -r requirements.yml

Once the role is installed you can set it up in your playbook.

    - hosts: load_balancer
      roles:
          - { role: ansible-haproxy }
      become: True

License
-------

GPL-3.0
