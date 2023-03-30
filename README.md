# How to flash a THINGZ Galaxia

1) install ESP-IDF 

 ```git clone -b v4.0.2 --recursive https://github.com/espressif/esp-idf.git``` as described in the documentation (https://bitbucket.org/thingz/micropython-galaxia/src/mass_storage/ports/esp32/)
 
 but go to the v4.3 branch, not the v4.2 as indicated in the tutorial
 
 follow the installation process and import ```export.sh```
 
 2) clone the micro-python-galaxia
 
 ```git clone https://ltoutain22@bitbucket.org/thingz/micropython-galaxia.git```
 
 then go to the mass_storage branch
 
 ```git checkout mass_storage```

go to the mpy-cross directory and compile

```cd mpy-croos```
```make```

go to ```ports/unix``` to download submodules, if directly done in ``ports/esp32``` not all the submodules are downloaded

```cd ports/unix```
```make submodules```

do this patch (https://lemariva.com/blog/2022/01/micropython-upgraded-support-cameras-m5camera-esp32-cam-etc)

```cd ../../lib/berkeley-db-1.xx/PORT/include/```c

and edit files bsd-queue.h, db.h, filevtable.h, mpool.h

to put the text inside a ```#include "text"```

go to ```ports/esp32``` and compile 

```make BOARD=GALAXIA```

execute the command at the end to flash the device. To put the device in a flashable mode, plug the USB while pushing the blue system button.



