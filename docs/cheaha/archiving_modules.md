# Archive old modules from LMOD path

This is the proposed method to archive modulefiles for old softwares that we don't want visible on [Cheaha](https://rc.uab.edu)

* Login as the ``build`` user.
* Go to the modulefile path for that particular software. 
* Create an ``.archive`` folder in that location.
  ```shell
  mkdir .archive
  ```
* Move the modulefiles you want to archive in the ``.archive`` directory.
  ```shell
  mv archived_modulefile.lua .archive
  ```
* Update the LMOD cache.
  ```shell
  update-lmod-cache.sh
  ```
