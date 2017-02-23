```
       _
__   _| |__   _____  __
\ \ / / '_ \ / _ \ \/ /
 \ V /| |_) | (_) >  <
  \_/ |_.__/ \___/_/\_\
```

# vbox

A streamlined interface for [VBoxManage](https://www.virtualbox.org/manual/ch08.html), the [VirtualBox](https://www.virtualbox.org/) command line tool.

`vbox` wraps `VBoxManage`, providing a simpler UI with a focus on frequently
used commands.

## Installation

### Homebrew

To install with [Homebrew](http://brew.sh/):

```bash
brew install alphabetum/taps/vbox
```

### bpkg

To install with [bpkg](http://www.bpkg.io/):

```bash
bpkg install alphabetum/vbox
```

### Manual

To install manually, simply add the `vbox` script to your `$PATH`. If
you already have a `~/bin` directory, you can use the following command:

```bash
curl -L https://raw.github.com/alphabetum/vbox/master/vbox \
  -o ~/bin/vbox && chmod +x ~/bin/vbox
```

## Usage

```
Usage:
  vbox commands [--raw]
  vbox config [--path]
  vbox forwarding add <vm-name> <rule-name> <port>
  vbox forwarding list <vm-name>
  vbox forwarding delete <vm-name> <rule-name>
  vbox (help [<command>] | -h | --help)
  vbox kill   (<name> | <uuid>)
  vbox list   [running | status]
  vbox manage [<general option>] <command>
  vbox pause  (<name> | <uuid>)
  vbox reset  (<name> | <uuid>)
  vbox resume (<name> | <uuid>)
  vbox show   (<name> | <uuid>)
  vbox start  (<name> | <uuid>) [--headless]
  vbox status [(<name> | <uuid>) [--long|-l]]
  vbox stop   (<name> | <uuid>)
  vbox (version | --version)

Global Options:
  -h --help  Display this help information.
  --version  Display version information.

Help:
  vbox help [<command>]
```

### Subcommands

#### `commands`

```
Usage:
  vbox commands [--raw]

Options:
  --raw  Display the command list without formatting.

Description:
  Display the list of available commands.
```

#### `config`

```
Usage:
  vbox config [--path]

Options:
  --path  Print the path to the configuration file, 'VirtualBox.xml'.

Description:
  When no argument has been passed, open the 'VirtualBox.xml' configuration
  file in `$EDITOR`, which is currently set to ''. When the
  `--path` option is specified, the path to 'VirtualBox.xml' is printed.
```

#### `forwarding`

```
Usage:
  vbox forwarding add <vm-name> <rule-name> <port>
  vbox forwarding list <vm-name>
  vbox forwarding delete <vm-name> <rule-name>

Subcommands:
  add     Add a new port forwarding rule.
  list    List forwarding rules.
  delete  Delete the specified rule.

Description:
  Manage port forwarding.

Example:
  vbox forwarding add "ubuntu-vm" "tcp5000" "5000"

  Equivalent of:
    VBoxManage controlvm ubuntu-vm \
      natpf1 "tcp5000,tcp,127.0.0.1,5000,,5000"
```

#### `help`

```
Usage:
  vbox help [<command>]

Description:
  Display help information for vbox or a specified command.
```

#### `kill`

```
Usage:
  vbox kill (<name> | <uuid>)

Description:
  Command: `VBoxManage controlvm <vm> poweroff`

  Has the same effect on a virtual machine as pulling the power cable on a real
  computer. The state of the VM is not saved beforehand, and data may be lost.
  (This is equivalent to selecting the "Close" item in the "Machine" menu of
  the GUI or pressing the window's close button, and then selecting "Power off
  the machine" in the dialog.)
```

#### `list`

```
Usage:
  vbox list [running | status]

Arguments:
  running  List all running VMs.
  status   Display all VMs with basic status information.

Description:
  List VirtualBox VMs.
```

#### `manage`

```
Usage:
  vbox manage [<general option>] <command>

Description:
  Alias for `VBoxManage`.

  VBoxManage Documentation:
    https://www.virtualbox.org/manual/ch08.html
```

#### `pause`

```
Usage:
  vbox pause (<name> | <uuid>)

Description:
  Command: `VBoxManage controlvm <vm> pause`

  Temporarily puts a virtual machine on hold, without changing its state for
  good. The VM window will be painted in gray to indicate that the VM is
  currently paused. (This is equivalent to selecting the "Pause" item in the
  "Machine" menu of the GUI.)
```

#### `reset`

```
Usage:
  vbox reset (<name> | <uuid>)

Description:
  Command: `VBoxManage controlvm <vm> reset`

  Has the same effect on a virtual machine as pressing the "Reset" button on a
  real computer: a cold reboot of the virtual machine, which will restart and
  boot the guest operating system again immediately. The state of the VM is not
  saved beforehand, and data may be lost. (This is equivalent to selecting the
  "Reset" item in the "Machine" menu of the GUI.)
```

#### `resume`

```
Usage:
  vbox resume (<name> | <uuid>)

Description:
  Command: `VBoxManage controlvm <vm> resume`

  Undo a previous pause command. (This is equivalent to selecting the "Resume"
  item in the "Machine" menu of the GUI.)
```

#### `show`

```
Usage:
  vbox show (<name> | <uuid>)

Description:
  Command: `VBoxManage showvminfo <vm>`

  Show information about a particular virtual machine.
```

#### `start`

```
Usage:
  vbox start (<name> | <uuid>) [--headless]

Description:
  Start the VM with the given name or UUID.
```

#### `status`

```
Usage:
  vbox status [(<name> | <uuid>) [--long|-l]]

Options:
  -l --long  Display long-form status information for the specified VM.

Description:
  When no argument has been passed, this acts as an alias for
  `vbox list status` and displays the status for all of the VMs. When
  passed a VM name or UUID, the status aka state of that VM is displayed.
```
#### `stop`

```
Usage:
  vbox stop (<name> | <uuid>)

Description:
  Command: `VBoxManage controlvm <vm> savestate`

  Save the current state of the VM to disk and then stop the VM. (This is
  equivalent to selecting the "Close" item in the "Machine" menu of the GUI or
  pressing the window's close button, and then selecting "Save the machine
  state" in the dialog.)
```

#### `version`

```
Usage:
  vbox (version | --version)

Description:
  Display the current program version.
```
