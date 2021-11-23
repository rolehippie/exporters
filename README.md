# exporters

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/exporters) [![Testing Build](https://github.com/rolehippie/exporters/workflows/testing/badge.svg)](https://github.com/rolehippie/exporters/actions?query=workflow%3Atesting) [![Readme Build](https://github.com/rolehippie/exporters/workflows/readme/badge.svg)](https://github.com/rolehippie/exporters/actions?query=workflow%3Areadme) [![Galaxy Build](https://github.com/rolehippie/exporters/workflows/galaxy/badge.svg)](https://github.com/rolehippie/exporters/actions?query=workflow%3Agalaxy) [![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/exporters)](https://github.com/rolehippie/exporters/blob/master/LICENSE) 

Ansible role to configure some Prometheus exporters. 

## Sponsor 

[![Proact Deutschland GmbH](https://proact.eu/wp-content/uploads/2020/03/proact-logo.png)](https://proact.eu) 

Building and improving this Ansible role have been sponsored by my employer **Proact Deutschland GmbH**.

## Table of content

* [Default Variables](#default-variables)
  * [blackbox_exporter_arch](#blackbox_exporter_arch)
  * [blackbox_exporter_args](#blackbox_exporter_args)
  * [blackbox_exporter_download](#blackbox_exporter_download)
  * [blackbox_exporter_version](#blackbox_exporter_version)
  * [blackbox_extra_modules](#blackbox_extra_modules)
  * [blackbox_general_modules](#blackbox_general_modules)
  * [exporters_available_tasks](#exporters_available_tasks)
  * [exporters_default_enabled](#exporters_default_enabled)
  * [exporters_extra_enabled](#exporters_extra_enabled)
  * [node_exporter_arch](#node_exporter_arch)
  * [node_exporter_args](#node_exporter_args)
  * [node_exporter_collector_directory](#node_exporter_collector_directory)
  * [node_exporter_download](#node_exporter_download)
  * [node_exporter_extra_collectors](#node_exporter_extra_collectors)
  * [node_exporter_general_collectors](#node_exporter_general_collectors)
  * [node_exporter_version](#node_exporter_version)
* [Dependencies](#dependencies)
* [License](#license)
* [Author](#author)

---

## Default Variables

### blackbox_exporter_arch

Architecture of the release to install

#### Default value

```YAML
blackbox_exporter_arch: "{{ 'arm64' if ansible_architecture == 'aarch64' else 'amd64'\
  \ }}"
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
blackbox_exporter_download: https://github.com/prometheus/blackbox_exporter/releases/download/v{{
  blackbox_exporter_version }}/blackbox_exporter-{{ blackbox_exporter_version }}.linux-{{
  blackbox_exporter_arch }}.tar.gz
```

### blackbox_exporter_version

Version of the release to install

#### Default value

```YAML
blackbox_exporter_version: 0.19.0
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
node_exporter_arch: "{{ 'arm64' if ansible_architecture == 'aarch64' else 'amd64'\
  \ }}"
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
node_exporter_download: https://github.com/prometheus/node_exporter/releases/download/v{{
  node_exporter_version }}/node_exporter-{{ node_exporter_version }}.linux-{{ node_exporter_arch
  }}.tar.gz
```

### node_exporter_extra_collectors

List of extra collectors to create

#### Default value

```YAML
node_exporter_extra_collectors: []
```

### node_exporter_general_collectors

List of general collectors to create

#### Default value

```YAML
node_exporter_general_collectors: []
```

### node_exporter_version

Version of the release to install

#### Default value

```YAML
node_exporter_version: 1.3.0
```

## Dependencies

* None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
