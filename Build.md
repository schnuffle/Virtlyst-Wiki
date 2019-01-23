# Build
This description has been extracted from a **[PR](https://github.com/cutelyst/Virtlyst/issues/14#event-2091559378)** comment made by [renlich](https://github.com/renlinch). I adopted the language and added some formating.
## Dependencies
Virtlyst uses the framework [Cutelyst](https://github.com/cutelyst/cutelyst/wiki/Installing-Cutelyst) from the same author and Cutelyst has been created with the Qt framework and cmake. so Virlyst has following dependencies:

- Qt >= 5.6
- Cmake >= 3.1
- Cutelyst >= 2.5

This docucment assumes you have Cutelyst already installed ( To install Cutelyst: [Cutelyst](https://github.com/cutelyst/cutelyst/wiki/Installing-Cutelyst) ).

For OpenSUSE,Fedora and CentOS there's a Repo you can use to install cutelyst: [Buschmann23 repo](https://software.opensuse.org/package/cutelyst2)

# Download and compile

- Download the [Release](https://github.com/cutelyst/Virtlyst/releases).
- Example V1.2.0 for me it is in "/home/usr/bin" :

>     ~ $> wget https://github.com/cutelyst/Virtlyst/archive/v1.2.0.tar.gz
    ~ $> tar xzf v1.2.0.tar.gz
    ~ $> cd Virtlyst-1.2.0/
    ~/Virtlyst-1.2.0 $> mkdir build
    ~/Virtlyst-1.2.0 $> cd build/
    ~/Virtlyst-1.2.0/build $> cmake ..
    ~/Virtlyst-1.2.0/build $> make
        [100%] Linking CXX shared library libVirtlyst.so
        [100%] Built target Virtlyst
    ~/Virtlyst-1.2.0/build $>
    
- When done copy or move it to where you would have it (Maybe there is a install routine but i didn't use it) to where you would have it. For me i leave it as it is. And run it with the Command as the user usr:

>     ~/Virtlyst-1.2.0/build $> cd ..
    ~/Virtlyst-1.2.0>cutelyst-wsgi2 --application ./build/src/libVirtlyst.so --chdir2 . --static-map static=root/static --http-socket localhost:3000 --master
        Installing EPoll event loop
        Cutelyst-WSGI starting
        WSGI socket 0 bound to TCP address 0.0.0.0:3000 fd 7
        Loading application: ./build/src/libVirtlyst.so
        30991:30991 cutelyst.core[warning] Can not load translations from not existing directory: "/usr/share/cutelyst2/translations"
        Changing directory2 to: .
        30991:30991 virtlyst[debug] Production false
        30991:30991 virtlyst[debug] Database "/home/usr/virtlyst.sqlite"
        30991:30991 virtlyst[debug] Creating database "/home/usr/virtlyst.sqlite"
        30991:30991 virtlyst[debug] PRAGMA journal_mode = WAL true ""
        30991:30991 virtlyst[critical] Created user admin with password: "xxxxxxxxx"
        30991:30991 cutelyst.core[warning] Can not load translations from not existing directory: "/usr/share/cutelyst2/translations"
        spawned WSGI master process (pid: 30991)
        spawned WSGI worker (and the only) (pid: 30995, cores: 1)
        30995:30995 virtlyst[debug] Database ready "virtlyst-0"
        Don't forget to note the initial Password for admin somewhere.
# Usage
Now it should work (for me it asks for root rights when executed as user, else you could run it as root.)
Access it via http://localhost:3000 from a browser of your choice.
For Internal Systems it worked until now on 12 Hosts as root user.

On the production machine i copied the root and application to /opt/virtlyst/. and replaced the execution with the other directory and run as root, binded at internal IP Address with no external access to others than the Administrators (via VPN).

