# Passenger

Originally borrowed from Geerling Guy

Installs Passenger (with Nginx) Ubuntu linux servers.

## Requirements

None.

## Using Ruby 3.x

Define the following variables:

```
install_ruby_from_source: true
ruby_version_override: "ruby-3.0.3"
```
## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    passenger_server_name: www.example.com

The server name (used in the Nginx virtual host configuration).

    passenger_app_root: /opt/example/public

The `passenger_root` for your application (e.g. the `public` folder in a rails app).

    passenger_app_env: production

The app environment passenger will load.

    passenger_root: /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini
    passenger_ruby: /usr/local/bin/ruby

Values for passenger configuration directives inside `nginx.conf`. These defaults should generally work correctly, but if you build `ruby` on its own (as an example), the path to ruby may be different.

    nginx_worker_processes: "{{ ansible_processor_vcpus | default(ansible_processor_count) }}"
    nginx_worker_connections: "768"
    nginx_keepalive_timeout: "65"
    nginx_remove_default_vhost: true

optional variable: `passenger_max_pool_size`: if you set this the role will set a number of passenger processes. passenger default is 6. also this will make the role pre-warm your site.


Nginx directives.

## Dependencies

None.

## Example Playbook

    - hosts: server
      roles:
        - { role: passenger }

## License

MIT / BSD

## Author Information

This role was originally created in 2015 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/). Any changes are now managed locally
