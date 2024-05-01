# Virtual Machine migration from one project to another

These instructions help in facilitating migration of a virtual machine from one project to another within OpenStack environment.

## Preparing of VM

Your virtual machine needs to be in Shut Down state before we start snapshotting the machine, so that there isn't a state change on the machine during the process. 

You can shut down the VM through the [web interface](https://cloud.rc.uab.edu).

## Create a snapshot of the VM

### Via CLI
* List the servers in your current project
  ```shell
  openstack server list
  ```
* Create a snapshot
  ```shell
  openstack server image create myInstance --name myInstanceSnapshot
  ```
* Check if the snapshot is in the list of images and in active status.
  ```shell
  openstack image list
  ```

### Via Web Interface
Follow the instructions [here](https://docs.openstack.org/horizon/latest/user/launch-instances.html#create-an-instance-snapshot)


## Download the snapshot
Copy the ID of snapshot you just took and use it below in place of myInstanceSnapshotID
```shell
openstack image save --file snapshot.raw myInstanceSnapshotID
```

## Import snapshot into the new project
### Via CLI
* Source openrc file for the new project
* Import snapshot
  ```shell
   openstack image create myInstanceSnapshot --disk-format qcow2 --container-format bare --private --file <snapshot-file>
  ```
### Via Web interface
Follow the instructions [here](https://docs.openstack.org/horizon/latest/user/manage-images.html)

## Create a new instance from the snapshot
### Via CLI
Launch an instance
```shell
openstack server create --flavor m1.medium --image myInstanceSnapshot --network dmznet myNewInstance
```

### Via Web Interface
Follow the instructions [here](https://docs.openstack.org/newton/user-guide/dashboard-launch-instances.html#launch-an-instance)



