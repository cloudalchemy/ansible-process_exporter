# Ansible Role: process_exporter

[![Build Status](https://travis-ci.com/cloudalchemy/ansible-process_exporter.svg?branch=master)](https://travis-ci.com/cloudalchemy/ansible-process_exporter)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-cloudalchemy.process_exporter-blue.svg)](https://galaxy.ansible.com/cloudalchemy/process_exporter/)
[![GitHub tag](https://img.shields.io/github/tag/cloudalchemy/ansible-process_exporter.svg)](https://github.com/cloudalchemy/ansible-process_exporter/tags)

## Description

Deploy [process-exporter](https://github.com/ncabatoff/process-exporter) using ansible.

Note. This repository and role uses the name process_exporter to conform with ansible galaxy constraints.

## Requirements

- Ansible >= 2.7 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `process_exporter_version` | 0.7.5 | Process exporter package version. Also accepts latest as parameter |
| `process_exporter_web_listen_address` | "0.0.0.0:9256" | Address on which process_exporter will listen |
| `process_exporter_config_dir` | "/etc/process_exporter" | Path to directory with process_exporter configuration |
| `process_exporter_names` | [see: defaults/main.yml](defaults/main.yml#L8) | Processes which should be monitored. Syntax is the same as in https://github.com/ncabatoff/process-exporter#using-a-config-file Default is consistent with deb/rpm packages.|

`process_exporter_names` handling has been set up in an unusual way to handle recommended process-exporter 'Template variables' (such as {{.Comm}}). Follow the example in [defaults/main.yml](defaults/main.yml) if you want to define custom filtering/grouping of processes that use Template variables and make sure to keep the {% raw %} block delimiters.

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - cloudalchemy.process_exporter
```

## Local Testing

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/ansible-community/molecule) (v3.x). You will have to install Docker on your system. See "Get started" for a Docker package suitable to for your system. Running your tests is as simple as executing `molecule test`.

## Continuous Integration

Combining molecule and circle CI allows us to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows use to create test scenarios for different role configurations. As a result we have a quite large test matrix which can take more time than local testing, so please be patient.

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## Troubleshooting

See [troubleshooting](TROUBLESHOOTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
