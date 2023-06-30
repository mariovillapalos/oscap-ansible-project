##1. AUDIT BEFORE PATCHING

# Perform an audit before applying patches
`ansible-playbook cis_rhel8_oscap.yml --tags "audit, <level-type>"`

Where <level-type> can be:
- rhel8_level1_server
- rhel8_level2_server
- rhel8_level1_workstation
- rhel8_level2_workstation

Example:
`ansible-playbook cis_rhel8_oscap.yml --tags "audit, rhel8_level1_server"` 


##2. PATCH

# Create a patch file
`ansible-playbook cis_rhel8_oscap.yml --tags "patch, <level-type>"`

# Run the patch file
`ansible-playbook <patch_file>`

Where <level-type> can be:
- rhel8_level1_server
- rhel8_level2_server
- rhel8_level1_workstation
- rhel8_level2_workstation

Where <patch_file> can be:
- patch_cis_server_l1.yml
- patch_cis_server_l2.yml
- patch_cis_workstation_l1.yml
- patch_cis_workstation_l2.yml

Example:
`ansible-playbook cis_rhel8_oscap.yml --tags "patch, rhel8_level1_server"`
`ansible-playbook --become -kK patch_cis_server_l1.yml`


##3. AUDIT AFTER PATCHING

# Perform an audit after applying patches
`ansible-playbook cis_rhel8_oscap.yml --limit rhel8 --become -kK --tags "audit, <level-type>"´

Where <level-type> can be:
- rhel8_level1_server
- rhel8_level2_server
- rhel8_level1_workstation
- rhel8_level2_workstation

Example:
´ansible-playbook cis_rhel8_oscap.yml --limit rhel8 --become -kK --tags "audit, rhel8_level1_server"´
