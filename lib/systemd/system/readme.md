## `firmware-rw.service` (`/boot/firwmare`)
Manages the Raspberry Pi's boot partition. Pulled in by `system-rw.service`.

## `root-rw.service` (`/`)
Manages the Raspberry Pi's root partition, pulled in by `system-rw.service`.

## `system-rw.service`
Virtual service for grouping managedsystem mounts, pulled in when `all-rw.service` is started. `RequiredBy` dependencies added so that it can be integrated into APT's timer tasks.

## `all-rw.service`
Virtual service for all managed mounts.

# Notes
- Services in this repository have their `RefuseManualStart`, `RefuseManualStop` and `StopWhenUnneeded` set to `true`, so that they will only start when depended on and not on user command, and stopped when no longer required. Addditional mounts can be managed, but must also specify these three directives for predictable behaviour.
