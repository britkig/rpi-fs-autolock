# Notes
- This package assumes that the root is not configured to automatically mount any partitions as writable, which is the default behaviour of the Linux kernel, as well as that scripts or no other package aims to achieve the same result.
- Services in this repository are not meant to be started and stopped manually, thus having `RefuseManualStart`, `RefuseManualStop` and `StopWhenUnneeded` all set to `true` in their `[Service]` sections. Addditional mounts can be managed/chained, but must also specify these three directives ato ensure correct remount timings.
## `firmware-rw.service` (`/boot/firwmare`)
Manages the Raspberry Pi's boot partition.

Pulled in by `system-rw.service`.
## `root-rw.service` (`/`)
Manages the Raspberry Pi's root partition.

Pulled in by `system-rw.service`.
## `system-rw.service`
Virtual service for grouping managed mounts essential to correct system functioning. `RequiredBy` dependencies added so that it can be integrated into APT's timer tasks if it is installed.

Pulled in when `all-rw.service` is started.
## `all-rw.service`
Virtual service for all managed mounts.
