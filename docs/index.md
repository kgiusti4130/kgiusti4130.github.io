# Welcome to KGiusti MKDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).



## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.
* `sample` - Just a sample line
* `sample2` - Just a sample line2

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.




# Arista tips and notes

#### Listing out code

```text
ls -l intended/configs
total 428
-rw-rw-r-- 1 avd avd 15168 May 31 18:51 1-sw-arista720XP-42-a.cfg
-rw-rw-r-- 1 avd avd 15168 May 31 18:52 1-sw-arista720XP-42-b.cfg
-rw-rw-r-- 1 avd avd 14653 Jun  1 18:35 1-sw-arista720XP-42-c.cfg
-rw-rw-r-- 1 avd avd 15168 May 31 18:52 1-sw-arista720XP-43-a.cfg
```

!!! danger annotate "Just a way to bring attention and also give annotations (1)"

    This is a simple paragraph with some notes, (2) This is just more
    info that can be written into the box.

1.  :man_raising_hand: I'm an annotation!
2.  :woman_raising_hand: I'm an annotation as well!   

#### Workflow for brining IDF online.
1. Build configs in AVD via build.yml playbook.
2. ZTP configs to switch.
3. Get switches online.
4. Use build.yml playbook to push any changes to switches that have happened since they have been powered off.
5. SCP certificate to switches in order to connect to CVP.
6. Verify switch shows up in CVP. Make sure switch is "provisioned".
7. Run cvp_deploy.yml to create container structure, move switch(es) to container and push tasks if there are any.

## Create a chart
### MPLS Core with MPLS EVPN, VPN-IPv4, VPN-IPv6

| Underlay | Overlay | Topology |
| -------- | ------- | -------- |
| ISIS-SR | iBGP | Arbitrary Mesh or leaf-spine |
| ISIS-SR + LDP | iBGP | Arbitrary Mesh or leaf-spine |
| ISIS + LDP | iBGP | Arbitrary Mesh or leaf-spine |
| OSPF + LDP | iBGP | Arbitrary Mesh or leaf-spine |

!!! Tip
    Some info that is useful can be written here.

## Known limitations

!!! Warning

    Input data and "structured_configs" will be in-place updated by various PyAVD functions.
    Make sure to deep copy the data first if modifications are not allowed.

## Roadmap

!!! note
    Subject to change. No commitments implied.

#### Create a list
- Add examples
- Add more tests (current coverage is 85%)
- Add network state validation similar to `eos_validate_state`.
- Add CloudVision tag integrations
- Make PyAVD the source of AVD logic and use as a dependency for the `arista.avd` Ansible collection.
- Explore support for custom Jinja2 templates.    


## More info

- **General** - General community discussion.
- **Ideas** - Ideas for new functionality that still needs to be prepared for a formal feature request.
- **Q&A** - Request help with installing or using AVD.

## Formatting that can be useful
## Final info
  - **Scopes**:

    - `{{ role_name }}`: AVD role impacted by PR. **Required** for `Feat`, `Cut`, and `Fix` types
    - `plugins`: To use when AVD plugin is impacted by PR. **Required** for `Feat`, `Cut`, and `Fix` types
    - `requirements`: To use when using the `Bump` type and when any AVD requirement is updated

    !!! info "Scopes"
        The scope is optional and can be ignored safely if your PR covers an undefined scope.

#### A simple way of doing annotations

Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
{ .annotate }

1.  :man_raising_hand: I'm an annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be expressed in Markdown.        

!!! note annotate "Phasellus posuere in sem ut cursus (1)"

    Lorem ipsum dolor sit amet, (2) consectetur adipiscing elit. Nulla et
    euismod nulla. Curabitur feugiat, tortor non consequat finibus, justo
    purus auctor massa, nec semper lorem quam in massa.

1.  :man_raising_hand: I'm an annotation!
2.  :woman_raising_hand: I'm an annotation as well!    

#### Another way of doing annotations with tabs

=== "Tab 1"

    Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
    { .annotate }

    1.  :man_raising_hand: I'm an annotation!

=== "Tab 2"

    Phasellus posuere in sem ut cursus (1)
    { .annotate }

    1.  :woman_raising_hand: I'm an annotation as well!



```yaml
# Login Banner
banners:
  motd: |
    You shall not pass. Unless you are authorized. Then you shall pass.
    EOF
```

???+ danger "Yes, that "EOF" is important!"
    Ensure the entire code snippet above is copied; including the `EOF`. This must be present for the configuration to be
    considered valid

## Create a drop down that can expand with code.

The `sites/site_1/inventory.yml` file should now look like the example below:

??? eos-config annotate "sites/site_1/inventory.yml"
    ``` yaml hl_lines="19-20"
    ---
    SITE1:
      children:
        CVP:
          hosts:
            cvp:
        SITE1_FABRIC:
          children:
            SITE1_SPINES:
              hosts:
                s1-spine1:
                s1-spine2:
            SITE1_LEAFS:
              hosts:
                s1-leaf1:
                s1-leaf2:
                s1-leaf3:
                s1-leaf4:
                s1-leaf5:
                s1-leaf6:
        SITE1_FABRIC_SERVICES:
          children:
            SITE1_SPINES:
            SITE1_LEAFS:
        SITE1_FABRIC_PORTS:
          children:
            SITE1_SPINES:
            SITE1_LEAFS:
    ```



## Start over with clean slate

Previously we downloaded and created a repository called `samplefiles`. Reset this repository to a directory by removing the hidden sub-directory `.git`.  This will remove any version control settings for the repository.

``` bash
cd /home/coder/project/labfiles/samplefiles
rm -rf .git   
```  

#### In case you want to add a question

??? question "Cows?"

    Yes! First, install cowsay: `sudo apt-get update && sudo apt-get install cowsay -y`
    Next, in the `ansible.cfg` file, set it to what should be the only acceptable setting, `nocows = False`.
    This feature is udderly ridiculous, and as much as I'd love to milk it for all the Dad jokes possible,
    I don't want to start any beef by delaying the workshop...Moo.

#### Formatting that we should be familiar with

Below is an example of the `ansible.cfg` located in our fork of the [Workshops](https://github.com/aristanetworks/ci-workshops-fundamentals.git "Fundamentals Workshop Repo on GitHub") repo:

??? eos-config annotate "Example Ansible Configuration File (~/project/labfiles/ci-workshops-fundamentals/ansible/ansible.cfg)"
    ```apache

    [defaults]

    # Disable host key checking by the underlying tools Ansible uses to connect to target hosts
    host_key_checking = False

    # Location of inventory file containing target hosts
    inventory = ./inventory/inventory.yml

    # Only gather Ansible facts if explicity directed to in a given play
    gathering = explicit

    # Disable the creation of .retry files if a playbook fails
    retry_files_enabled = False

    # Path(s) to search for installed Ansible Galaxy Collections
    collections_paths = ~/.ansible/collections

    # Enable additional Jinja2 Extensions (https://jinja.palletsprojects.com/en/3.1.x/extensions/)
    jinja2_extensions =  jinja2.ext.loopcontrols,jinja2.ext.do,jinja2.ext.i18n

    # Enable the YAML callback plugin, providing much easier to read terminal output. (https://docs.ansible.com/ansible/latest/plugins/callback.html#callback-plugins)
    stdout_callback = yaml

    # Permit the use of callback plugins when running ad-hoc commands
    bin_ansible_callbacks = True

    # List of enabled callbacks. Many callbacks shipped with Ansible are not enabled by default
    callback_whitelist = profile_roles, profile_tasks, timer

    # Maximum number of forks that Ansible will use to execute tasks on target hosts
    forks = 15

    # Disable cowsay (Why?)
    nocows = True

    [paramiko_connection]
    # Automatically add the keys of target hosts to known hosts
    host_key_auto_add = True

    [persistent_connection]
    # Set the amount of time, in seconds, to wait for response from remote device before timing out persistent connection.
    command_timeout = 60

    # Set the amount of time, in seconds, that a persistent connection will remain idle before it is destroyed.
    connect_timeout = 60

    ```



???+ info
    The `ansible-galaxy collection list` command is supported in Ansible 2.10+

This will yield output similar to below:

??? eos-config annotate "Ansible Galaxy Collection List"
    ```powershell

    # /home/coder/.ansible/collections/ansible_collections
    Collection        Version
    ----------------- -------
    ansible.netcommon 4.1.0
    ansible.posix     1.4.0
    ansible.utils     2.8.0
    arista.avd        3.6.0
    arista.cvp        3.4.0
    arista.eos        6.0.0
    community.general 6.2.0

    ```

#### Add a tip with emojis & computer keys!
???+ tip
    :writing_hand: In VS Code, you can toggle comments on/off by selecting the text and pressing ***windows*** ++ctrl++ + ++slash++ or ***mac*** ++cmd++ + ++slash++.

???+ tip
    This will show the differences between the current device configuration
    and the configuration before we did our `make deploy` command.                

???+ tip
    Daisy chaining "Makesies" is a great way to run a series of tasks with a single CLI command :grinning:    


### Highlight lines of code

#### Highlight lines 2 and 4
``` py hl_lines="2 4"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

#### Works on yaml too highlight lines 1-3 & 5
``` yaml hl_lines="1-3 5"
l3spine:
  defaults:
    platform: 7020SR
    loopback_ipv4_pool: 10.44.35.21/30
    mlag_peer_ipv4_pool:  10.44.52.0/31
    mlag_peer_l3_ipv4_pool: 10.44.52.2/31
```

## Adding keyboard keys
++ctrl+alt+del++


#### Add annotations to inline code
``` yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.

``` bash
interface Ethernet1
   no switchport # (1)
   no shutdown # (2)
 
```

1.  :man_raising_hand: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.
2.  Brings the port up into an operational state.

#### code block with annotation stripped

``` yaml
interface Ethernet1
   no switchport # (1)!
   no shutdown # (2)!
```

1.  Look ma, less line noise!
2.  Nice and quiet

#### Remove copy button from text box

```{ .text .no-copy }
total 428
-rw-rw-r-- 1 avd avd 15168 May 31 18:51 1-sw-arista720XP-42-a.cfg
-rw-rw-r-- 1 avd avd 15168 May 31 18:52 1-sw-arista720XP-42-b.cfg
-rw-rw-r-- 1 avd avd 14653 Jun  1 18:35 1-sw-arista720XP-42-c.cfg
-rw-rw-r-- 1 avd avd 15168 May 31 18:52 1-sw-arista720XP-43-a.cfg
```

#### Testing only copy portion of text box (not working yet)


```bash
Ansible Galaxy Collection List
```

<div class="embed-result">
```
Collection        Version
----------------- -------
ansible.netcommon 4.1.0
ansible.posix     1.4.0
ansible.utils     2.8.0
arista.avd        3.6.0
arista.cvp        3.4.0
arista.eos        6.0.0
community.general 6.2.0
```

</div>