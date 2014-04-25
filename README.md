# Assembly-Guard

Watching for files modifications in a given path, automatically run `make` and prettify the output (errors, warnings) for a better assembly-development environment.

![image](https://dl.dropboxusercontent.com/u/4041100/github/conmake.jpg)

## Installation
The script uses ``inotify-tools`` linux package, so it should be installed before running the script.

1. install **inotify-tools**:
```sudo apt-get install inotify-tools```

2. [download the script here](http://) (right click & save), and put it in your working directory.
3. run the following command: ``./watch .``

make sure that you have ``makefile`` in that directory.

If you're a bad programmer like me, you should see something like this:
![image](https://dl.dropboxusercontent.com/u/4041100/github/assemblyguard_output.jpg)


### For Vagrant users

If you're using linux in [Vagrant](http://www.vagrantup.com) environment, inotify-tools will not working properly, because vagrant shared folders is NFS shares, which doesn't support inotify events.

The workaround for that is **vagrant rsync folders**, which is supported since vagrant 1.5 (so update your vagrant to the last release first!).

Config your shared folder to use rsync: In you ``VagrantFile`` config rsync as any other synced folder, by just specifying the "rsync" type:

`config.vm.synced_folder "/shared_folder_host_path", "/vm_path", type: "rsync"`

Then, open another console tab and run ``vagrant rsync-auto`` command in the background, for auto sync the shared folder with the VM via rsync.