# Importing a Target Cluster

This process is documented in the in the MCM KnowledgeCenter here:

https://www.ibm.com/support/knowledgecenter/en/SSFC4F_1.1.0/mcm/manage_cluster/import_gui.html



### On the MCM Hub

1. Login to the MCM Console on the MCM Hub server:

   https://icp-console.<domainname>/multicloud

2. From the menu in the upper-right hand corner navigate to the  **Clusters** page

3. Select the **Add cluster** button

4. Click **Import an existing cluster**

5. Enter a meaningful cluster name into the **Cluster name** field. Enter the same value in the **Namespace** field.

   **Note:** This value cannot be changed once the cluster is imported.

   Click **Generate command**

6. On the Command Generated screen click the copy command icon to copy the full command.



### On the Target Cluster

1. SSH to the Target Cluster and login as a user with cluster-admin privileges

2. Make sure your `kubectl`cli environment is configured (.i.e run `kubeclt get nodes`)

3. Paste the command you copied from step 6 above and paste it into the console and hit return

4. You can monitor the installation of the MCM endpoint code by checking the status of the pods in the `multicluster-endpoint` namespace with the command `kubectl get po -n multicluster-endpoint`

   ```
   NAME                                                  READY   STATUS    RESTARTS   AGE
   endpoint-appmgr-68bdb647bf-5zjwz                      2/2     Running   3          20d
   endpoint-appmgr-helm-crd-5b8c9fcfbf-df2wh             2/2     Running   4          7d18h
   endpoint-certmgr-7ff5945bb9-8v27j                     1/1     Running   0          20d
   endpoint-component-operator-74cbcb967-4c8gv           1/1     Running   0          20d
   endpoint-connmgr-6d44d8f6c6-sndwz                     1/1     Running   0          20d
   endpoint-policyctrl-55869f6d58-r447z                  2/2     Running   1          20d
   endpoint-search-74dbb5d5ff-ft6xs                      1/1     Running   104        20d
   endpoint-svcreg-868c86bfbb-p4rxm                      1/1     Running   0          20d
   endpoint-svcreg-coredns-655c4bd978-s688n              1/1     Running   0          20d
   endpoint-tiller-564977955-f2tr6                       1/1     Running   0          20d
   endpoint-topology-weave-collector-6c6f6b8d79-m64tv    1/1     Running   0          20d
   endpoint-topology-weave-scope-5vqss                   1/1     Running   0          20d
   endpoint-topology-weave-scope-app-76db4f955-l9rf7     2/2     Running   0          20d
   endpoint-topology-weave-scope-kqmkv                   1/1     Running   0          20d
   endpoint-topology-weave-scope-qh5k8                   1/1     Running   0          20d
   endpoint-workmgr-66cc844d86-jftbx                     1/1     Running   0          20d
   ibm-multicluster-endpoint-operator-5bf5b888c8-4bmxv   1/1     Running   0          20d
   monitoring-prometheus-operator-69ffd5f89-d5spq        2/2     Running   0          20d
   prometheus-monitoring-prometheus-0                    4/4     Running   1          20d
   ```

   Once all the pods are `Running`  return to the MCM Hub Console and return to the Clusters page and you should see your new cluster listed.