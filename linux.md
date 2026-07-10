# linux 

## Update System

```bash
sudo apt update
sudo apt upgrade -y
sudo apt full-upgrade -y
```

## Alias

```bash
alias <shortcut_command>=<'original_command'>
```

Eg:
```bash
alias cls='clear'
alias gs='git status'
alias gb='git branch'
```

Add the following in `~/.bashrc`

```bash
nano ~/.bashrc
```

View Environment Variables

```bash
printenv
```

or

```bash
env
```
Finally source bashrc

```bash
source ~/.bashrc
```

## Open Google Chrome with webpage from terminal

```bash
google-chrome "https://www.google.com"
```

## Notification Send

```bash
notify-send "TITLE" "MESSAGE"
```

## Message over Terminal

```bash
zenity --info --title="TITLE" --text="MESSAGE"
```

If over SSH

```bash
DISPLAY=:1 zenity --info --title="TITLE" --text="MESSAGE"
```

```bash
DISPLAY=:1 \
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u <USER ID>)/bus \
zenity --info --title="TITLE" --text="MESSAGE"
```

### Prevention

```bash
sudo systemctl stop ssh
```

```bash
sudo systemctl start ssh
```

## SSH Without IP on Local Network

```bash
Username@SystemName.local
```

**PRANK**

```bash
google-chrome "https://www.amazon.in/Babique-Teddy-Bear-Soft-Birthday/dp/B08HZFCCNT?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=A2GTG1HPYW8M2P"
```

```bash
notify-send "Reminder to Buy Teddy" "Buy Teddy for her😊"
```

```bash
zenity --info --title="Reminder to Buy Teddy" --text="Bro BUY Teddy for her Now 🧸"
```

```bash
DISPLAY=:1 zenity --info --title="Reminder to Buy Teddy" --text="Bro BUY Teddy for her Now 🧸"
```

```bash
DISPLAY=:1 \
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/$(id -u <USER ID>)/bus \
zenity --info --title="Reminder to Buy Teddy" --text="Bro BUY Teddy for her Now 🧸"
```


## Logged-in Users & Sessions

Displays all users currently logged into the system

```bash
who
```

Show only your current login session:

```bash
who am i
```

*Note this is different from `whoami`


## Show Active Sessions

Displays users along with command, cpu usage, uptime, system laod.

```bash
w
```

## Show Current Terminal

Displays the terminal associated with the current shell.

```bash
tty
```


## Kill a Terminal Session

First, identify the target terminal using `who` and `w`.

Terminate all processes attached to a terminal:

```bash
pkill -t pts/0
```

- `tty*`: Local logins
- `pts/*`: SSH session terminals
- `seat0`: Local graphical desktop session
- `:1`: | X11 graphical display session

**⚠️ Warning:** Running `pkill -t tty2` on a desktop system will terminate the graphical session and log out the user.

