# Notes
- This package assumes that systemd is used as the `init` subsystem and that no partitions are configured by other means to be writable by-default, which is the default behaviour of the kernel.
- Services in this repository are not meant to be started and stopped manually, thus having `RefuseManualStart`, `RefuseManualStop` and `StopWhenUnneeded` all set to `true` in their `[Service]` sections. Addditional mounts can be managed/chained, but must also follow the same convention for predictable behaviour.
