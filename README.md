# 386bsd0.1-c

This is part III of an automated redo of http://gunkies.org/wiki/Installing_386BSD_on_BOCHS. Due to time constraints within Travis it is not possible to redo the full guide in a single repository. For part I see https://github.com/dugoh/386bsd0.1.

Prebuild binary for qemu 0.11 is pulled in together with the disk image from part II. The second patchkit is installed and GENERICISA is compiled . After this a full buildworld is done.

All artifacts are pushed to https://dugoh.github.io/386bsd0.1-c/. The disk is bzip2 compressed and then split into 50MB parts. Grabbing the disk is simple.

```
for i in a b c; do \
  wget -O - https://dugoh.github.io/386bsd0.1-c/qdisk.part-a${i};\
done|bunzip2 >qdisk.img
```

For hints on how to build qemu 0.11 on a modern system see https://github.com/dugoh/oldqemu

386BSD with all patchkits installed should run in qemu 0.11 with:

```
qemu -L /usr/local/share/qemu/ \
     -curses                   \
     -hda qdisk.img            \
     -M isapc                  \
     -net nic                  \
     -no-reboot                \
     -m 64                     \
     -startdate "1994-04-22"'
```

# Warning

This is being maintained with github and travis-ci as the IDE, I don't do branches and have no qualms using master as a scratch pad. Hic Sunt Leones, here be dragons, buyer beware, sorry for the ugly commit messages and all that.

# Current build status

-    Part I    
[![Build Status](https://travis-ci.org/dugoh/386bsd0.1.svg?branch=master)](https://travis-ci.org/dugoh/386bsd0.1)

-    Part II   
[![Build Status](https://travis-ci.org/dugoh/386bsd0.1-b.svg?branch=master)](https://travis-ci.org/dugoh/386bsd0.1-b)

-    Part III   
[![Build Status](https://travis-ci.org/dugoh/386bsd0.1-c.svg?branch=master)](https://travis-ci.org/dugoh/386bsd0.1-c)
