# Shell Commands

## Message a User

The `write` command can be used to message a user on the same node. The command takes 2 arguments, the `USER` followed by the user's terminal. Ex: `write blaze pts/3`

The command allows you to enter one or more lines of text and is sent by pressing `CTRL D`.

The following command will message the user on all of their terminals:

```shell
user=blaze
for term in $(w $user | grep $user | awk '{print $2}'); do
  echo "Please do not run jobs on the login node" | write $user $term;
done
```

## Extend TimeLimit for a Job

Occassionaly, we will get a request from a user to extend the `TimeLimit` for a job(s).

>>>
`TimeLimit=<time>`
The job's time limit. Output format is `[days-]hours:minutes:seconds` or "`UNLIMITED`". Input format (for update command) set is `minutes`, `minutes:seconds`, `hours:minutes:seconds`, `days-hours`, `days-hours:minutes` or `days-hours:minutes:seconds`. Time resolution is one minute and second values are rounded up to the next minute. If changing the time limit of a job, either specify a new time limit value or precede the time and equal sign with a "`+`" or "`-`" to increment or decrement the current time limit (e.g. "`TimeLimit+=30`"). In order to increment or decrement the current time limit, the JobId specification must precede the `TimeLimit` specification. Note that incrementing or decrementing the time limit for a job array is only allowed before the job array has been split into more than one job record.
>>>

Example: Extend the `TimeLimit` for three jobs by 10 more days

```shell
for job in 15202444 15202445 15202446; do
  scontrol show job $job | grep TimeLimit | awk '{print $2}'
  scontrol update jobid=$job TimeLimit=+10-00
  scontrol show job $job | grep TimeLimit | awk '{print $2}'
done
```
**Note:** Job Arrays can't be incremented / decremented and must modified with absolute runtimes. For example, to extend a job with a `TimeLimit` of 1 day 2 hours by an additional day, you would use `TimeLimit=2-02:00:00`

## Fix User Directories and Slurm Account

The following is code you can use to fix, if necessary, one or more users directories and Slurm accounts.

You can either specify the number of users to `tail` from `getent passwd` to fix/verify the X most recently created accounts. Alternately, comment out the first `users=`, uncomment the second `users=` and add users space delimited

```shell
num_users=20
users="$(getent passwd | tail -n ${num_users} | awk -F: '{print $1}' | tr '\n' ' ')"
#users='blaze uabrules'
#users="`echo ${users} | tr '[:upper:]' '[:lower:]'`"

for user in `echo $users` ; do
  echo $user
  sudo /cm/shared/apps/slurm/current/bin/sacctmgr --immediate add Account $user
  sudo /cm/shared/apps/slurm/current/bin/sacctmgr --immediate add User Accounts=$user $user
  
  dir=/home/$user
  if [ ! -d $dir ]; then
    echo "Creating directory $dir"
    sudo cp -a /etc/skel $dir
    sudo chown -R ${user}:${user} $dir
    sudo chmod 700 $dir
  else
    sudo chown -R ${user}:${user} $dir
    sudo chmod 700 $dir
  fi
  unset dir
  for dir in /data/user/$user /scratch/$user /data/temporary-scratch/$user; do
    if [ ! -d $dir ]; then
      echo "Creating directory $dir"
      sudo mkdir $dir
      sudo chown ${user}:${user} $dir
      sudo chmod 700 $dir
    else
      sudo chown -R ${user}:${user} $dir
      sudo chmod 700 $dir
    fi
  done
  
  for dir in /home/$user /data/user/$user /scratch/$user /data/temporary-scratch/$user; do
    ls -ld $dir
  done
done

unset users num_users
```
