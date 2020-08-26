Kubernetes Role Cluster
-----------------------

Prerequisites
-------------

* ansible
* git
* Two AWS VMs: master-node and worker-node

Configuration
-------------

1. download the project in each other nodes
   on the master node and worker node, 
   
   ```
   * git clone https://github.com/franck-art/kubernetes-playbook.git
   * cd kubernetes-playbook/kubernetes_role_cluster/
   * ansible-galaxy install  -r roles/requirements.yml
   ```

2. Configuration in master node
* configure the ip address in **groups_vars/all.yml** file and **hosts** file 
* launch playbook

` ansible-playbook --private-key vars/devops.pem  -i hosts  launch.yml --ask-vault-pass `

3. Command to Join cluster node (worker node)
* copy     the command in **/home/centos/join_message** file in the end of file and and execute the command in the *worker-node*

4. Open the ports: **6443 and 8285**

5. Verify the connection between master and node
   
   ```
      **sudo kubectl get nodes**
        NAME          STATUS   ROLES    AGE   VERSION
        master-node   Ready    master   82m   v1.19.0
        worker-node   Ready    <none>   66m   v1.19.0
   ```
