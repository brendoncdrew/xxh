<p align="center">
  <p align="center">
    <b>xxh</b> is for using Python-powered <a href="https://xon.sh/">xonsh shell</a> wherever you go through the ssh.
  </p>
</p>
<p align="center">  
  <a href="https://pypi.org/project/xonssh-xxh/" target="_blank" alt="PyPI Latest Release"><img src="https://img.shields.io/pypi/v/xonssh-xxh.svg"></a>
 <a href="https://asciinema.org/a/osSEzqnmH9pMYEZibNe2K7ZL7" target="_blank"><img alt="asciinema demo" src="https://img.shields.io/badge/demo-asciinema-grass"></a>
  <img alt="PyPI - License" src="https://img.shields.io/pypi/l/xonssh-xxh">
</p>
<p align="center">
Spread the word about xxh! Click ⭐ on the repo and share the link! 
</p>

## Installation
```
python3 -m pip install --upgrade xonssh-xxh
```
After install you can just using `xxh` command as replace `ssh` to connecting to the host because `xxh` has seamless support of basic `ssh` command arguments. 

## Usage
```
$ xxh --help                                                                                                                 
usage: xxh [config name from ssh config]

usage: xxh [ssh arguments] [user@]host[:port] [xxh arguments]

usage: xxh [-h] [-V] [-p SSH_PORT] [-l SSH_LOGIN] [-i SSH_PRIVATE_KEY] [-o SSH_OPTION -o ...] 
           [user@]host[:port]
           [+i] [+if] [+lxh LOCAL_XXH_HOME] [+hxh HOST_XXH_HOME] [+he HOST_EXECUTE_FILE] 
           [+m METHOD] [+v] [+vv]

The xxh is for using the xonsh shell wherever you go through the ssh. 

     ____  __________     @    @    
  ______  /          \     \__/     
   ____  /    ______  \   /   \           contribution
 _____  /    / __   \  \ /   _/   https://github.com/xonssh/xxh   
   ___ (    / /  /   \  \   /          
        \   \___/    /  /  /                plugins            
      ___\          /__/  /   https://github.com/search?q=xxh-plugin
     /    \________/     /                           
    /___________________/       

required arguments:
  [user@]host[:port]    Destination may be specified as [user@]host[:port] or server name from ~/.ssh/config

common arguments:
  -h, --help            show this help message and exit
  --version, -V         show program's version number and exit

ssh arguments:
  -p SSH_PORT           Port to connect to on the remote host.
  -l SSH_LOGIN          Specifies the user to log in as on the remote machine.
  -i SSH_PRIVATE_KEY    File from which the identity (private key) for public key authentication is read.
  -o SSH_OPTION -o ...  SSH options are described in ssh man page. Example: -o Port=22 -o User=snail

xxh arguments:
  +i, ++install         Install xxh to destination host.
  +if, ++install-force  Removing the host xxh home and install xxh again.
  +lh LOCAL_XXH_HOME, ++local-xxh-home LOCAL_XXH_HOME
                        Local xxh home path. Default: ~/.xxh
  +hh HOST_XXH_HOME, ++host-xxh-home HOST_XXH_HOME
                        Host xxh home path. Default: ~/.xxh
  +he HOST_EXECUTE_FILE, ++host-execute-file HOST_EXECUTE_FILE
                        Execute script file placed on host and exit
  +m METHOD, ++method METHOD
                        Portable method: appimage
  +v, ++verbose         Verbose mode.
  +vv, ++vverbose       Super verbose mode.
```

## Plugins

**xxh plugin** is the set of xsh scripts which will be run when you'll use xxh. You can create xxh plugin with your lovely aliases, tools or color theme and xxh will bring them to your ssh sessions.

🔎 [Search xxh plugins on Github](https://github.com/search?q=xxh-plugin&type=Repositories)

💡 [Create xxh plugin](https://github.com/xonssh/xxh-plugin-sample)

📌 Pinned plugins:

* [Pipe Liner](https://github.com/xonssh/xxh-plugin-pipe-liner) — processing the lines easy with python and classic shell pipes
* [Bar Theme](https://github.com/xonssh/xxh-plugin-theme-bar) — theme to stay focused
* [Autojump](https://github.com/xonssh/xxh-plugin-autojump) — save time on moving thru directories

## Notes

### Using pip and python

The xxh xonsh will use pip and python from `xonsh.AppImage` by default. You can install pip packages ordinally with `pip install`. They will appear in `$XXH_HOME/pip`.

### How it works?

When you run `xxh <host>` command:

1. If it needed xxh will download portable xonsh shell and store locally to future use. 

2. If it needed xxh upload the portable xonsh to the host (`~/.xxh` by default) along with init scripts and plugins.

3. Finally xxh will make ssh connection to the server and run portable xonsh shell without any addition installs and affection on the target host.

## Development
Use [xxh-tests](https://github.com/xonssh/xxh-tests) environment for development and contribution.

### Known Issues

#### GLIBs versions

Current method to make xonsh portable is using an [AppImage](https://appimage.org/) which was built on [manylinux2010 (PEP 571)](https://github.com/niess/linuxdeploy-plugin-python/issues/12). In case you see the error like ``/xonsh-x86_64.AppImage: /lib/x86_64-linux-gnu/libc.so.6: version GLIBC_2.25 not found (required by /ppp/xonsh-x86_64.AppImage)`` this means you should rebuild the AppImage for older version of linux distributive. Try [linuxdeploy-plugin-python](https://github.com/niess/linuxdeploy-plugin-python/).

#### WSL1: ^Z

```
# xxh YT-1300
^Z
# 
```
This issue was addressed to Xonsh team in [3367](https://github.com/xonsh/xonsh/issues/3367). Just try to run command again.

#### Related issues

What will make xxh more universal and stable in the future:
* [AppImages run on Alpine](https://github.com/AppImage/AppImageKit/issues/1015) 
* [Fix xonsh for WSL1](https://github.com/xonsh/xonsh/issues/3367)

## Thanks
* @scopatz for https://github.com/xonsh/xonsh
* @probonopd for https://github.com/AppImage
* @niess for https://github.com/niess/linuxdeploy-plugin-python/
* @gforsyth for https://github.com/xonsh/xonsh/issues/3374
