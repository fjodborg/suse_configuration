# suse_configuration

This is my configuration for Opensuse. I used Gnome as the preset.

## Install nvidia drivers

```bash
# The newest version (570.144) as of writing this had issues.
sudo zypper in nvidia-video-G06=570.133.07-33.1
sudo zypper in nvidia-compute-utils-G06=570.133.07-33.1
sudo zypper al nvidia-compute-G06 nvidia-driver-G06-kmp-default nvidia-video-G06
```

## Cosmic DE
``` bash
sudo zypper ar --refresh https://download.opensuse.org/repositories/X11:COSMIC:Next/openSUSE_Factory/X11:COSMIC:Next.repo
sudo zypper refresh
sudo zypper in patterns-cosmic-cosmic
```

## KDE DE
```bash
sudo zypper install sddm
sudo zypper in -t pattern kde kde_plasma
sudo update-alternatives --config default-displaymanager 
# Possibly i also need to add DISPLAYMANAGER=sddm inside /etc/sysconfig/displaymanager
```

now logout and choose the user. Then in the bottom right corner select the cogwheel and select cosmic and login

## Install git and generate ssh key.
Just follow githubs guide...

## Setup fn keys

### temporary fix (Current session)
```bash
echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
```

### Permanent fix 
```bash
echo "options hid_apple fnmode=2" | sudo tee /etc/modprobe.d/hid_apple.conf
sudo dracut --regenerate-all --force
```

and reboot to take effect. 

### Steam
``` bash
sudo zypper in steam
```

login and enable compatiblity with all library games and select proton 10.0.1 beta

### .bashrc
```bash
echo "export EDITOR=nano" | tee -a $HOME/.bashrc
```

### Vscode 
``` bash
sudo zypper in opi
opi vscode
```

```
code --install-extension ms-python.python
code --install-extension rust-lang.rust
code --install-extension tamasfe.even-better-toml
code --install-extension ms-vscode.cpptools
```



### media Codec
```bash
sudo zypper in opi
opi codecs
```


### Misc
``` bash
sudo zypper in discord htop
```
