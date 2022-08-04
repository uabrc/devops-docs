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

Example: Extend the `TimeLimit` for three jobs by 10 days

```shell
for job in 15202444 15202445 15202446; do
  scontrol show job $job | grep TimeLimit | awk '{print $2}'
  scontrol update jobid=$job TimeLimit=+10-00
  scontrol show job $job | grep TimeLimit | awk '{print $2}'
done
```
