# docker-ce

This role enables to innstall docker-ce on a system.

## Requirements

No requirements.

## Role Variables

| Name                                      | Type    | Location            | Description                                                                                                        |
| ----------------------------------------- | ------- | ------------------- | ------------------------------------------------------------------------------------------------------------------ |
| docker_ce_version                         | string  | `defaults/main.yml` | The version of Docker to install. Defaults to `20.10.6`.                                                           |
| docker_ce_centos_yum_repository_url       | string  | `defaults/main.yml` | The base URL of Docker yum repository. Defaults to `https://download.docker.com/linux/centos`.                     |
| docker_ce_sysctl_enable_ip_forwarding     | boolean | `defaults/main.yml` | A flag to enable IP Forwarding in sysctl. Defaults to `yes`.                                                       |
| docker_ce_daemon_settings                 | string  | `defaults/main.yml` | The Docker daemon options which will be written to `/etc/docker/daemon.json`. See below for default configuration. |
| docker_compose_releases_url               | string  | `defaults/main.yml` | The base URL to download Docker Compose. Defaults to `https://github.com/docker/compose/releases/download`.        |
| docker_compose_version                    | string  | `defaults/main.yml` | The version of Docker-Compose to install. Defaults to `1.29.2`.                                                    |
| docker_compose_arch                       | string  | `defaults/main.yml` | The architecture of Docker-Compose to install. Defaults to `Linux-x86_64`.                                         |
| docker_compose_executable_sha256_checksum | string  | `defaults/main.yml` | The expected checksum of the docker-compose executable downloaded from the website.                                |
| docker_compose_executable                 | string  | `vars/main.yml`     | The local path where to install docker-compose executable. Defaults to `/usr/local/sbin/docker-compose`.           |

By default, the `/etc/docker/daemon.json` will be configured as-is:

```json
{
  "debug": false,
  "log-level": "info",
  "exec-opts": ["native.cgroupdriver=systemd"]
}
```

Configure `docker_ce_daemon_settings` to add more configuration.

## Dependencies

No dependencies.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: julb.docker_ce }
```

## License

MIT

## Author Information

More to find on my [Github](https://github.com/julb).

## Contributing

This project is totally open source and contributors are welcome.

When you submit a PR, please ensure that the syntax has been checked.
