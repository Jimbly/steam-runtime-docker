steam-runtime-docker
====================

Docker images with the 32-bit Linux runtime environment built by 
https://github.com/ValveSoftware/steam-runtime.  These are intended to be used
to make Linux builds for Steam games on a Windows host.

*Note: I'm only using the _GCC_ version myself, CLANG versions are untested*

Sources Dockerfiles
* [jimbly/steamrt-precise-base](steamrt-precise-base/README.md) - just barebones Ubuntu 12.04 sourced from the Steam repo
* [jimbly/steamrt-i386](steamrt-i386-gcc/Dockerfile) - steamrt and build-essentials added in (used by all below)
* [jimbly/steamrt-i386-gcc](steamrt-i386-gcc/Dockerfile) GCC 4.8
* [jimbly/steamrt-i386-clang-3.4](steamrt-i386-clang-3.4/Dockerfile) CLANG 3.4
* [jimbly/steamrt-i386-clang-3.6](steamrt-i386-clang-3.6/Dockerfile) CLANG 3.6

Prerequisites - Windows
* Latest Docker not recommended because it breaks the ability to run any other VMs on your system :(, so, [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/) instead (though this should all be able to be made to work on vanilla Docker)
* Install Docker Toolbox
* * If you already have Git/Bash and VirtualBox installed, you can skip those steps
* * * You'll probably need to fix the "Docker Quickstart Terminal" shortcut to point to where you have Git/Bash installed
* Linux host (or VM) only needed if you want to re-generate steamrt-precise-base

If you want to resize the VM disk to more than the default 20GB (it auto-grows to this limit, it won't actually take 100gb if you set the max to 100gb), open Docker Quickstart Terminal.
* A steamrt image takes around 1.7GB, I easily used 20GB while debugging Docker containers, but only end up using about 5GB (including Docker's internal stuff) to just build the example Dockerfile
* WARNING: this will delete all existing Docker images and containers!
* `docker-machine.exe stop default`
* `docker-machine rm default`
* `docker-machine create -d virtualbox --virtualbox-disk-size "100000" default`

To actually use these images, open your favorite terminal to the example/ folder
* `docker-machine.exe stop default`
* In VirtualBox, for the VM named "default" go to Settings..., Shared Folders, add path of "C:\" mapping to "C" (capital is important for easier scripting), Auto-mount
* `docker-machine.exe start default`
* `docker-machine.exe env --shell=cmd default` - get these variables into your environment via copy and paste or following the instructions
* `docker build -t steamrt-example .`
* `docker run -it --rm -v /C/:/C steamrt-example bash`
* You should then be able to navigate to any folder, and starting doing builds. Any changes you make (outside of to /C, which is simply mounted) are discarded when you exit your session, if you want to make configuration changes, edit _Dockerfile_ and re-build the image.
* To build something non-interactively from Windows, (e.g. in a Visual Studio build step):
* * `docker run -i --rm -v /C/:/C steamrt-example bash -c "mkdir -p /C/SRC/MyProject/build/ && cd /C/SRC/MyProject/build && cmake .. && make"`
