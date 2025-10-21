# exporters

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/exporters)
[![General Workflow](https://github.com/rolehippie/exporters/actions/workflows/general.yml/badge.svg)](https://github.com/rolehippie/exporters/actions/workflows/general.yml)
[![Readme Workflow](https://github.com/rolehippie/exporters/actions/workflows/docs.yml/badge.svg)](https://github.com/rolehippie/exporters/actions/workflows/docs.yml)
[![Galaxy Workflow](https://github.com/rolehippie/exporters/actions/workflows/galaxy.yml/badge.svg)](https://github.com/rolehippie/exporters/actions/workflows/galaxy.yml)
[![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/exporters)](https://github.com/rolehippie/exporters/blob/master/LICENSE)
[![Ansible Role](https://img.shields.io/badge/role-rolehippie.exporters-blue)](https://galaxy.ansible.com/rolehippie/exporters)

Ansible role to configure some Prometheus exporters.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of content

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [blackbox_exporter_arch](#blackbox_exporter_arch)
  - [blackbox_exporter_args](#blackbox_exporter_args)
  - [blackbox_exporter_download](#blackbox_exporter_download)
  - [blackbox_exporter_version](#blackbox_exporter_version)
  - [blackbox_extra_modules](#blackbox_extra_modules)
  - [blackbox_general_modules](#blackbox_general_modules)
  - [exporters_available_tasks](#exporters_available_tasks)
  - [exporters_default_enabled](#exporters_default_enabled)
  - [exporters_extra_enabled](#exporters_extra_enabled)
  - [node_exporter_arch](#node_exporter_arch)
  - [node_exporter_args](#node_exporter_args)
  - [node_exporter_collector_directory](#node_exporter_collector_directory)
  - [node_exporter_download](#node_exporter_download)
  - [node_exporter_extra_collectors](#node_exporter_extra_collectors)
  - [node_exporter_general_collectors](#node_exporter_general_collectors)
  - [node_exporter_version](#node_exporter_version)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.10`

## Default Variables

### blackbox_exporter_arch

Architecture of the release to install

#### Default value

```YAML
blackbox_exporter_arch: "{{ 'arm64' if ansible_architecture == 'aarch64' or ansible_architecture
  == 'arm64' else 'amd64' }}"
```

### blackbox_exporter_args

List of arguments joined for the executable

#### Default value

```YAML
blackbox_exporter_args: []
```

### blackbox_exporter_download

URL to the archive of the release to install

#### Default value

```YAML
blackbox_exporter_download: 
  https://github.com/prometheus/blackbox_exporter/releases/download/v{{ 
  blackbox_exporter_version }}/blackbox_exporter-{{ blackbox_exporter_version 
  }}.linux-{{ blackbox_exporter_arch }}.tar.gz
```

### blackbox_exporter_version

Version of the release to install

#### Default value

```YAML
blackbox_exporter_version: 0.27.0
```

### blackbox_extra_modules

Extra module configuration injected plain into the config

#### Default value

```YAML
blackbox_extra_modules:
```

### blackbox_general_modules

General module configuration injected plain into the config

#### Default value

```YAML
blackbox_general_modules:
  http_2xx:
    prober: http
  post_2xx:
    prober: http
    http:
      method: POST
```

### exporters_available_tasks

#### Default value

```YAML
exporters_available_tasks:
  - node
  - blackbox
```

### exporters_default_enabled

List of default enabled exporters

#### Default value

```YAML
exporters_default_enabled:
  - node
```

### exporters_extra_enabled

List of available exporter tasks

#### Default value

```YAML
exporters_extra_enabled: []
```

### node_exporter_arch

Architecture of the release to install

#### Default value

```YAML
node_exporter_arch: "{{ 'arm64' if ansible_architecture == 'aarch64' or ansible_architecture
  == 'arm64' else 'amd64' }}"
```

### node_exporter_args

List of arguments joined for the executable

#### Default value

```YAML
node_exporter_args: []
```

### node_exporter_collector_directory

Directory for static textfile collector

#### Default value

```YAML
node_exporter_collector_directory: /var/cache/node-exporter
```

### node_exporter_download

URL to the archive of the release to install

#### Default value

```YAML
node_exporter_download: 
  https://github.com/prometheus/node_exporter/releases/download/v{{ 
  node_exporter_version }}/node_exporter-{{ node_exporter_version }}.linux-{{ 
  node_exporter_arch }}.tar.gz
```

### node_exporter_extra_collectors

List of extra collectors to create

#### Default value

```YAML
node_exporter_extra_collectors: []
```

#### Example usage

```YAML
node_exporter_extra_collectors:
  - name: example
    content: |
      echo "works"
    interval: 60
    boot: 60
    state: present
  - name: example-from-url
    url: http://example.com/script.txt
    interval: 60
    boot: 60
  - name: example-from-template
    src: path/to/template.j2
    interval: 60
    boot: 60
  - name: remove-old-script
    state: abbsent
```

### node_exporter_general_collectors

List of general collectors to create

#### Default value

```YAML
node_exporter_general_collectors: []
```

#### Example usage

```YAML
node_exporter_general_collectors:
  - name: example
    content: |
      echo "works"
    interval: 60
    boot: 60
    state: present
  - name: example-from-url
    url: http://example.com/script.txt
    interval: 60
    boot: 60
  - name: example-from-template
    src: path/to/template.j2
    interval: 60
    boot: 60
  - name: remove-old-script
    state: abbsent
```

### node_exporter_version

Version of the release to install

#### Default value

```YAML
node_exporter_version: 1.9.1
```

## Discovered Tags

**_blackbox_**

**_exporters_**

**_node_**

**_{{ exporters_available_tasks + ['exporters'] }}_**

## Dependencies

- None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
