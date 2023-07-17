# 1. AUDIT BEFORE PATCHING

## Perform an audit before applying patches
`ansible-playbook <playbook-filename> --tags "audit, <level-type>"`

Where "playbook-filename" can be:
- cis_rhel8_oscap.yml if you are working in an online environment
- cis_rhel8_oscap_offline.yml if you are working in an offline environment

Where "level-type" can be:
- rhel8_level1_server
- rhel8_level2_server
- rhel8_level1_workstation
- rhel8_level2_workstation

Example:
`ansible-playbook cis_rhel8_oscap.yml --tags "audit, rhel8_level1_server"` 


# 2. PATCH

## Create a patch file
`ansible-playbook <playbook-filename> --tags "patch, <level-type>"`

Where "playbook-filename" can be:
- cis_rhel8_oscap.yml if you are working in an online environment
- cis_rhel8_oscap_offline.yml if you are working in an offline environment

Example:
`ansible-playbook cis_rhel8_oscap.yml --tags "patch, rhel8_level1_server"`

## Run the patch file
`ansible-playbook --become -kK <patch_file>`

Where "level-type" can be:
- rhel8_level1_server
- rhel8_level2_server
- rhel8_level1_workstation
- rhel8_level2_workstation

Where "patch_file" can be:
- patch_cis_server_l1.yml
- patch_cis_server_l2.yml
- patch_cis_workstation_l1.yml
- patch_cis_workstation_l2.yml

Example:
`ansible-playbook --become -kK patch_cis_server_l1.yml`


# 3. AUDIT AFTER PATCHING

## Perform an audit after applying patches
`ansible-playbook <playbook-filename> --limit rhel8 --become -kK --tags "audit, <level-type>"`

Where "playbook-filename" can be:
- cis_rhel8_oscap.yml if you are working in an online environment
- cis_rhel8_oscap_offline.yml if you are working in an offline environment

Where "level-type" can be:
- rhel8_level1_server
- rhel8_level2_server
- rhel8_level1_workstation
- rhel8_level2_workstation

Example:
`ansible-playbook cis_rhel8_oscap.yml --limit rhel8 --become -kK --tags "audit, rhel8_level1_server"`
