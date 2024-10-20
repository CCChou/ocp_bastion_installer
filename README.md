OpenShift Bastion Node Installer
=========

Install the dns, loadbalancer, http server and generate the ignition files automatically.

P.S.
For install the whole OpenShift Cluster automatically, you can use the following project
- https://github.com/RedHatOfficial/ocp4-vsphere-upi-automatio

Requirements
------------

Ansible 2.6+

Role Variables
--------------
    # enable or disable
    firewalld_enable: true
    selinux_enable: true
    dns_configure: true
    haproxy_configure: true

    # the upper nameserver
    dns: 168.95.1.1
    
    # define the cluster name for cluster
    clusterName: ocp4
    
    # define the base domain for cluster
    baseDomain: example.com

    # define the resource files absolute path
    pullSecretDir: /root/pull-secret.txt
    sshKeyDir: /root/.ssh/id_rsa.pub
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
    - name: master01
      ip: 10.9.42.33
    - name: master02
      ip: 10.9.42.34
    - name: master03
      ip: 10.9.42.35
    worker:
    - name: worker01
      ip: 10.9.42.36
    - name: worker02
      ip: 10.9.42.37


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: bastion
      vars_files:
      - env.yml
      roles:
      - ocp_bastion_installer
