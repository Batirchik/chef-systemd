# systemd chef cookbook [![Build Status](https://travis-ci.org/nathwill/chef-systemd.svg?branch=master)][travis]

A resource-drive [Chef][chef] cookbook for [systemd][docs]. Currently under
construction; see issues for list of ways to contribute :)

Cookbook builds on a core systemd_unit resource in order to provide resources
for the following unit types:

- automount
- device
- mount
- path
- service
- slice
- socket
- swap
- target
- timer

Recommended reading:
- This README!
- [Overview of systemd for RHEL 7][rhel]
- [systemd docs][docs]
- [Lennart's blog series][blog]
- libraries under `libraries/*.rb`
- test cookbooks under `test/fixtures/cookbooks/setup`

## Recipes


## Resources

### Foreword

#### Unit basics

[Systemd units][units] are files that describe a system resource, like a
socket, a device, a service, etc. They're written in [INI][ini] format, an
easy and readable format for describing simple configurations.

Admin-generated configurations are stored under '/etc/systemd/system', and
override system-level units located under '/usr/lib/systemd/system'.

Every unit type supports at least a "Unit" and "Install" section. The "Unit"
section carries information about the unit itself, that does not vary between
unit types; attributes like "Requires", "Description", "Conflicts", or
assertions about the unit's expectations about its environment. The "Install"
section carries information about the unit installation, and is only used by
systemd when a unit is enabled or disabled; attributes like "Wants" or "Alias".

Almost every unit unit type (with a couple minor exceptions in device and
target), also support a configuration section based on their own "type". For
example, service units have service-specific configuration in the "Service"
section for configuration options like "ExecStart", and mount units have a
"Mount" section for options like "What", and "Where".

There are also 3 special groups of unit options that are common between several
types of units: exec, kill, and resource-control, which handle common options
re: execution environment configuration (e.g. "WorkingDirectory"), process
killing procedure configuration (e.g. "KillSignal"), and resource control
settings (e.g. "MemoryLimit"). Resources which support these attributes along
with their type-specific attributes are explicitly noted in the resource
documentation below, and linked to the documentation for those attributes.

Hey! That sounds pretty easy, right?

### systemd_automount

### systemd_device

### systemd_mount

### systemd_path

### systemd_service

### systemd_slice

### systemd_socket

### systemd_swap

### systemd_target

### systemd_timer

## Common Attributes

### kill

### exec

### resource-control


[blog]: http://0pointer.de/blog/projects/systemd-for-admins-1.html
[chef]: https://chef.io
[docs]: http://www.freedesktop.org/wiki/Software/systemd/
[ini]: https://en.wikipedia.org/wiki/INI_file
[rhel]: https://access.redhat.com/articles/754933
[travis]: https://travis-ci.org/nathwill/chef-systemd
[units]: http://www.freedesktop.org/software/systemd/man/systemd.unit.html
