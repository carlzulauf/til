# Find Open Ports

Forget if you've already launched a service? Wondering if a port number is already being used? Want to know what process is using that port you want to bind to? Well, `netstat` will answer most of those questions.

Find all processes (l)istening on (t)cp ports, showing us (n)umeric ports only (no guessing protocol/service based on port number) with the (p)id/process-name.

```
$ netstat -ltnp
```

PID and process name are only available for processes owned by the current user. Prepend `sudo` to see PID/names for all.
