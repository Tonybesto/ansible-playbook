Playbook project

# ---
# - hosts: all
# - import_playbook: ../static-assignments/common.yml
# - import_playbook: ../static-assignments/common-del.yml

# - hosts: uat-webservers
# - import_playbook: ../static-assignments/uat-webservers.yml

---
# - hosts: all
#   name: Include dynamic variables 
#   tasks:
#     - import_playbook: ../static-assignments/common.yml 
#     - include: ../dynamic-assignments/env-vars.yml
#   tags:
#     - always

# - hosts: webservers
#   name: Webserver assignment
#   tasks:
#     - import_playbook: ../static-assignments/webservers.yml

# - hosts: lb
#   name: Loadbalancers assignment
#   tasks:
#     - import_playbook: ../static-assignments/loadbalancers.yml
#   when: load_balancer_is_required
  # - hosts: lb
  # - name: Loadbalancers assignment
  #   import_playbook: ../static-assignments/loadbalancers.yml
  #   when: load_balancer_is_required


---
- name: import common file
  import_playbook: ../static-assignments/common.yml
  tags:
     - always

- name: import loadbalancer file
  import_playbook: ../static-assignments/loadbalancers.yml


- name: import webservers file
  import_playbook: ../static-assignments/webservers.yml

- name: include env-vars file
  import_playbook: ../dynamic-assignments/env-vars.yml
  tags:
      - always