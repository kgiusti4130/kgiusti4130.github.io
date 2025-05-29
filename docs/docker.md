# Suggested dev container settings

#### devcontainer.json

??? eos-config annotate "devcontainer.json"
    ``` yaml hl_lines="2 6"
    {
    	"name": "<my_org_name>-dev01",
    	"context": ".",
    	"workspaceFolder": "/workspace",
    	"dockerComposeFile": "docker-compose.yml",
    	"service": "<my_org_name>-dev01",
    	"extensions": [
    		"redhat.vscode-yaml",
    		"ms-python.python",
    		"github.vscode-pull-request-github",
            "lextudio.restructuredtext",
            "aristapublisher.eos",
            "samuelcolvin.jinjahtml",
            "eamodio.gitlens",
    		"PKief.material-icon-theme",
    		"johnpapa.vscode-peacock",
    		"DavidAnson.vscode-markdownlint",
    		"ms-azuretools.vscode-docker",
    		"hilleer.yaml-plus-json",
    		"docsmsft.docs-yaml",
    		"GraphQL.vscode-graphql"
    	],
    	"shutdownAction": "stopCompose"
    }
    ```

#### docker-compose.yml

??? eos-config annotate "devcontainer.json"
    ``` yaml hl_lines="4 6-7"
    version: "3.9"
    
    services:
      <my_org_name>-dev01:
        build: .
        image: "<my_org_name>-dev01:latest"
        container_name: <my_org_name>-dev01
        # restart: always
        restart: no
        command: ['tail', '-f', '/dev/null']
        network_mode: "host"
    
        environment:
          - TZ=America/New_York
          - DEBIAN_FRONTEND=noninteractive
          - LC_ALL=UTF-8
        volumes:
          - ../:/workspace
    ```

#### requirements.txt

??? eos-config annotate "Ansible Galaxy Collection List"
    ```bash
    ansible-core==2.16.2
    ansible-lint
    ansible-pylibssh
    #anta==0.10.0   #Use for ANTA & AVD integration
    anta==0.11.0   #Use for running ANTA standalone
    aristaproto>=0.1.1
    asgiref
    certifi
    cffi
    chardet
    click
    colorama
    cryptography>=38.0.4
    cvprac>=1.3.1
    deepmerge>=1.1.0
    future
    idna
    importlib-resources
    jsonschema>=4.5.1,<4.18
    Jinja2>=3.0.0
    MarkupSafe
    md-toc>=7.1.0
    netaddr>=0.7.19
    netmiko
    packaging
    paramiko
    psutil
    pre-commit
    pycparser
    pynetbox
    pyparsing
    pyez
    pytz
    PyYAML>=6.0.0
    requests>=2.27.0
    six
    sqlparse
    treelib>=1.5.5
    urllib3
    zipp
    ```


#### requirements.yml

??? eos-config annotate "Ansible Galaxy Collection List"
    ```bash
    ---
    collections:
    
      - name: arista.avd
        version: 4.7.1
        source: https://galaxy.ansible.com

      - name: cisco.asa
        source: https://galaxy.ansible.com
    
      - name: cisco.ios
        source: https://galaxy.ansible.com        
    
      - name: ansible.netcommon
        version: 6.0.0
        source: https://galaxy.ansible.com
    
      - name: ansible.posix
        source: https://galaxy.ansible.com
    
      - name: ansible.utils
        source: https://galaxy.ansible.com
    
      - name: community.general
        source: https://galaxy.ansible.com
    
      - name: netbox.netbox
        source: https://galaxy.ansible.com
    ```