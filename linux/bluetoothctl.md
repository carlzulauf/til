# bluetoothctl

Like everything in linux, you can control bluetooth from the command line. This is made pretty easy by it's obvious name and decent builtin documentation.

Running `bluetoothctl --help` gives enough info to understand the basics.

## Find a device and disconnect

Sometimes I want to connect headphones to a different computer, but I'm already sitting or laying down in another room from the machine they are paired with. When I turn the headphones on they connect with the machine I'm not using.

I can ssh to all of my machines, so this ends up being pretty easy:

```
near$ ssh far-away-machine

far$ bluetoothctl devices
Device 40:8E:2C:34:EA:A8 Xbox Wireless Controller
Device 40:8E:2C:34:EA:A9 Xbox Wireless Controller

far$ bluetoothctl disconnect 40:8E:2C:34:EA:A9
Attempting to disconnect from 40:8E:2C:34:EA:A9
...
Successful disconnected
```
