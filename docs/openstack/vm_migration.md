# Virtual Machine Migration From One Project to Another

These instructions help in facilitating migration of a virtual machine from one project to another within OpenStack environment.

## Preparing of VM

Your virtual machine needs to be in Shut Down state before we start snapshotting the machine, so that there isn't a state change on the machine during the process.

You can shut down the VM through the [web interface](https://cloud.rc.uab.edu).

## Create a Snapshot of the VM

### Create Snapshot via CLI

- List the servers in your current project

  ```shell
  openstack server list
  ```

- Create a snapshot

  ```shell
  openstack server image create myInstance --name myInstanceSnapshot
  ```

- Check if the snapshot is in the list of images and in active status.

  ```shell
  openstack image list
  ```

### Create Snapshot via Web Interface

Follow the instructions at the [OpenStack Documentation](https://docs.openstack.org/horizon/latest/user/launch-instances.html#create-an-instance-snapshot).

## Download the Snapshot

Copy the ID of snapshot you just took and use it below in place of myInstanceSnapshotID

```shell
openstack image save --file snapshot.raw myInstanceSnapshotID
```

## Import Snapshot Into the New Project

### Import Snapshot via CLI

- Source openrc file for the new project

- Import snapshot

  ```shell
   openstack image create myInstanceSnapshot --disk-format qcow2 --container-format bare --private --file <snapshot-file>
  ```

### Import Snapshot via Web Interface

Follow the instructions [OpenStack Documentation](https://docs.openstack.org/horizon/latest/user/manage-images.html)

## Create a New Instance From the Snapshot

### Create Instance via CLI

Launch an instance

```shell
openstack server create --flavor m1.medium --image myInstanceSnapshot --network dmznet myNewInstance
```

### Create Instance via Web Interface

Follow the instructions [OpenStack Documentation](https://docs.openstack.org/newton/user-guide/dashboard-launch-instances.html#launch-an-instance)
