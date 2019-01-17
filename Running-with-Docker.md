# Running with Docker on Linux Mint 19/Ubuntu 18.04

## Process

* Make sure Docker is installed  
* Clone the repo: `git clone https://github.com/cutelyst/Virtlyst.git virtlyst`
* Build the image and name it: `cd virtlyst; docker -t virtlyst build .`
* Once the build is done you'll have a image called *virtlyst*
* To be able to access the host's libvirt and the web panel some stuff has to be mapped:

    ```
    docker run -ti --init --name virtlyst -p 3000:3000 -v /run/libvirt:/run/libvirt:rw virtlyst
    ```

## Logging in

Connect to <http://x.x.x.x:3000/>

The username is "admin".  The password is generated randomly, and is displayed in the container logs at startup.

Create a connection of type "Local socket", with any name you like, and you'll be able to see the VMs running on this host.
