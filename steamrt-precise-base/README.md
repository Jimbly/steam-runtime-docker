jimbly/steamrt-precise-base
===========================

Prerequisites:
* Linux host (any distro, any version, in a VM is fine)
* Windows host
* * Latest Docker not recommended because it breaks the ability to run any other VMs on your system -_-, so, Docker Toolbox instead (though this should all be able to be made to work on vanilla Docker)
* * Install Docker Toolbox
* * * If you already have Git/Bash and VirtualBox installed, you can skip those steps
* * * * You'll probably need to fix the "Docker Quickstart Terminal" shortcut to point to where you have Git/Bash installed

On a linux host:
* Run `setup_chroot_minimal.sh --i386` to generate precise_i386.tgz
* Run `setup_chroot_minimal.sh --amd64` to generate precise_amd64.tgz

On Windows...

In Docker Quickstart Terminal, if you want to resize the VM to more than 20GB
* A steamrt image/container takes around 1.7GB, I easily used 20GB while debugging Docker containers, end up using about 5GB (including Docker's internal stuff) to just build this Dockerfile
* WARNING: this will delete all existing Docker images and containers!
* `docker-machine.exe stop default`
* `docker-machine rm default`
* `docker-machine create -d virtualbox --virtualbox-disk-size "100000" default`

Open your favorite terminal to this folder
* `docker-machine.exe env --shell=cmd default` - get these variables into your environment via copy and paste or following the instructions
* `docker import X:\precise_i386.tgz jimbly/steamrt-precise-base`
* `docker import X:\precise_amd64.tgz jimbly/steamrt-precise-amd64-base`

Links
=====
* [This image on Docker Hub](https://hub.docker.com/r/jimbly/steamrt-precise-base/)
* https://github.com/ValveSoftware/steam-runtime
