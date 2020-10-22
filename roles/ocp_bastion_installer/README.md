OpenShift Bastion Node Installer
=========

Install the dns, loadbalancer, http server and generate the ignition files automatically

Requirements
------------

Ansible 2.6+

Role Variables
--------------

    # the upper nameserver
    dns: 168.95.1.1
    
    # define the cluster name for cluster
    clusterName: ibm
    
    # define the base domain for cluster
    baseDomain: cp.example

    # define the resource files absolute path
    pullSecretDir: /root/pull-secret.txt
    sshKeyDir: /root/.ssh/id_rsa.pub
    rawfileDir: /root/rhcos-4.4.3-x86_64-metal.x86_64.raw.gz
    ocpInstallDir: /root/openshift-install-linux.tar.gz
    ocpClientDir: /root/openshift-client-linux.tar.gz
    
    # define ip and hostname for all nodes
    bastion:
      name: bastion
      ip: 10.9.42.31
    bootstrap:
      name: bootstrap
      ip: 10.9.42.32
    master:
    - name: master0
      ip: 10.9.42.33
    - name: master1
      ip: 10.9.42.34
    - name: master2
      ip: 10.9.42.35
    worker:
    - name: infra
      ip: 10.9.42.36
    - name: worker
      ip: 10.9.42.37


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: bastion
      vars_files:
      - env.yml
      roles:
      - ocp_bastion_installer
