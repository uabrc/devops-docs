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
