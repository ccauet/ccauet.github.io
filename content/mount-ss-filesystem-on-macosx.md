Title: Mount an SSH filesystem on MacOS X
Date: 2012-07-31 10:44
Author: Christophe

1. Install newest stable releases of FUSE for OS X (OSXFUSE) and SSHFS: [osxfuse.github.com](http://osxfuse.github.com)

2. Create a dedicated mountpoint, e.g.:    
<code>mkdir ~/Mountpoint</code>

3. Mount remote file system using:    
<code>sshfs $USER@$HOST:/path/to/foo ~/Mountpoint</code>

4. See the man page for a list of all possible options. My standard configuration is:     
<code>sshfs $USER@$HOST:/path/to/foo ~/Mountpoint -o auto_cache,reconnect,volname=$SOMENAME</code>

5. If you have an .ssh/config defining an alias for the remote machine, but sshfs seems to ignore it, you can try:
<code>sshfs $ALIAS:/path/to/foo ~/Mountpoint -F ~/.ssh/config</code>

6. Finally:    
<code>sshfs $USER@$HOST:/path/to/foo ~/Mountpoint -F ~/.ssh/config -o auto_cache,reconnect,volname=$SOMENAME</code>

7. To unmount, just type:   
<code>umount -f ~/Mountpoint</code>

**If you want a GUI, install the MacFusion App after step 1**:   
[macfusionapp.org](http://macfusionapp.org)

SSH Filesystem official webpage:   
[fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

man page sshfs   
[linux.die.net/man/1/sshfs](http://linux.die.net/man/1/sshfs)
