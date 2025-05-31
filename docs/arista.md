
# **Arista tips and notes**

#### Push files from one switch to another via MGMT vrf using bash

```text
cli vrf MGMT
bash scp /mnt/flash/EOS-4.32.5M.swi admin@10.1.252.121:/mnt/flash/
```

#### Push files from one switch to another via MGMT vrf using cli

```text
bash scp /mnt/flash/Pristine-EOS-4.32.5M.swi admin@10.178.7.51:/mnt/flash/EOS-4.32.5M.swi
```

??? annotate "Commands to verify TerminAttr"
    ```bash
    show version detail | grep TerminAttr-core
    show daemon TerminAttr
    show agent TerminAttr logs | no
    ```

#### Run multiple watch diff commands at same time

```text
watch 1 diff run show int status conn | nz;!;!; show lldp nei
```

#### Commit Timer TLDR

```text
config session bgp1
```

#### Make config changes

```text
commit timer 00:02:00
show configuration sessions
configure session bgp1 commit
```
