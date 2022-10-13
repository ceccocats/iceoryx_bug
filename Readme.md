# ICEORYX bug 
to be tested with ros2-galatic

# build
```
source setup.sh
colcon build --packages-up-to demo_nodes_cpp
```

# run roudi
```
gdb --ex run --args /opt/ros/galactic/bin/iox-roudi -c roudi_config.toml
```

# run talker
```
ros2 run demo_nodes_cpp talker_loaned_message
```

# run listener
```
ros2 run demo_nodes_cpp listener
```

# kill listener
```
pkill listener 
```

# roudi output
```
cecco@seb:ws$ gdb --ex run --args /opt/ros/galactic/bin/iox-roudi -c roudi_config.toml 
GNU gdb (Ubuntu 9.2-0ubuntu1~20.04) 9.2
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /opt/ros/galactic/bin/iox-roudi...
Reading symbols from /usr/lib/debug/.build-id/1c/d4a876b927bdd18fe6094967128e145a304923.debug...
Starting program: /opt/ros/galactic/bin/iox-roudi -c roudi_config.toml
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
Log level set to: [Warning]
2022-10-14 00:32:54.437 [Warning]: IPC channel still there, doing an unlink of roudi
SharedMemory still there, doing an unlink of /iceoryx_mgmt
Reserving 123083640 bytes in the shared memory [/iceoryx_mgmt]
[ Reserving shared memory successful ] 
SharedMemory still there, doing an unlink of /cecco
Reserving 168000000 bytes in the shared memory [/cecco]
[ Reserving shared memory successful ] 
[New Thread 0x7fffe5fc5700 (LWP 1328665)]
[New Thread 0x7fffe57c4700 (LWP 1328666)]
[New Thread 0x7fffe4fc3700 (LWP 1328667)]
[New Thread 0x7fffe47c2700 (LWP 1328668)]
[New Thread 0x7fffe3fc1700 (LWP 1328669)]
RouDi is ready for clients

Thread 5 "Mon+Discover" received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7fffe47c2700 (LWP 1326019)]
iox::mepoo::SharedChunk::decrementReferenceCounter (this=0x7fffe47bfb10) at /usr/include/c++/9/bits/atomic_base.h:549
549           fetch_sub(__int_type __i,
(gdb) 
```