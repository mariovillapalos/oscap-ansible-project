Tipos de ejecucion

###### AUDIT BEFORE PATCHING ######

ansible-playbook cis_rhel8_oscap.yml --tags "audit, <level-type>"

where <level-type>:
    - rhel8_level1_server
    - rhel8_level2_server
    - rhel8_level1_workstation
    - rhel8_level2_workstation

E.g: 
    - ansible-playbook cis_rhel8_oscap.yml --tags "audit, rhel8_level1_server"

###### PATCH ######
1. Creates patch file:
    - ansible-playbook cis_rhel8_oscap.yml --tags "patch, <level-type>"

2. Run patch file:
    - ansible-playbook <patch_file> 

where <level-type>:
    - rhel8_level1_server
    - rhel8_level2_server
    - rhel8_level1_workstation
    - rhel8_level2_workstation

where <patch_file>:

    - patch_cis_server_l1.yml
    - patch_cis_server_l2.yml
    - patch_cis_workstation_l1.yml
    - patch_cis_workstation_l2.yml

E.g: 
    - ansible-playbook cis_rhel8_oscap.yml --tags "patch, rhel8_level1_server"
    - ansible-playbook --become -kK patch_cis_server_l1.yml


###### AUDIT AFTER PATCHING ######

ansible-playbook cis_rhel8_oscap.yml --limit rhel8 --become -kK --tags "audit, <level-type>"

where <level-type>:
    - rhel8_level1_server
    - rhel8_level2_server
    - rhel8_level1_workstation
    - rhel8_level2_workstation

E.g:
    - ansible-playbook cis_rhel8_oscap.yml --limit rhel8 --become -kK --tags "audit, rhel8_level1_server"