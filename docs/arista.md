# Arista

### SCP push files to Arista

``` bash
scp EOS-4.30.4M.swi username@10.76.23.11:/mnt/flash/
``` 

???+ tip
    1. Make sure aaa authorization is set to something like `aaa authorization exec default local`  
    2. If you need to use a different vrf you can do something like `cli vrf MGMT` 


## Update TerminAttr on switch

### Push file to switch
``` bash
scp TerminAttr-1.19.4-1.swix wandyn@10.0.4.141:/mnt/flash/
``` 

### Install the extension
``` bash
copy flash:TerminAttr-1.19.4-1.swix extension:
conf
extension TerminAttr-1.19.4-1.swix
copy installed-extensions boot-extensions
daemon TerminAttr
shutdown
no shutdown
``` 

!!! note annotate "Commands for verification"
    1. `show daemon TerminAttr`
    2. `show version detail | grep TerminAttr-core`
    3. `show agent TerminAttr logs | no`


### ANTA testing

``` bash
anta \
    --username test \
    --password test \
    --enable \
    --inventory clab_anta_inventory.yml \
    nrfu --catalog clab_anta_tests.yml table
```
<div class="embed-result">
```
╭────────────────────── Settings ──────────────────────╮
│ Running ANTA tests:                                  │
│ - ANTA Inventory contains 6 devices (AsyncEOSDevice) │
│ - Tests catalog contains 12 tests                    │
╰──────────────────────────────────────────────────────╯    

```
</div>