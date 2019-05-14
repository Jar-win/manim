Installation
============

Manim runs on Python's version 3.7. Earlier versions of python are not supported. Manim is avilable as a python package and can be installed through pip via
``pip install manimlib`` or ``python3 -m pip install manimlib``.

manim relies on system libraries you will need to install on your operating
system:

* ffmpeg
* latex
* sox
* cairo

Installation (System Libraries)
-----------
* **Linux**

Installation of system libraries on linux is the easiest.

*Debian Based distribution (Ubuntu/Linux mint etc)*
```
$ sudo apt install libcairo2-dev ffmpeg sox texlive-full 
```


*RedHat/Cent OS Based distribution*
```
$ sudo dnf install cairo-devel ffmpeg sox texlive-scheme-full
```
The `texlive-scheme-full` installation in quite big, but it will have `all the packages required by manim <https://github.com/3b1b/manim/blob/master/manimlib/tex_template.tex>`_.

* **Windows**

1. Install FFmpeg : https://www.wikihow.com/Install-FFmpeg-on-Windows.
2. Install Cairo: Download the wheel from https://www.lfd.uci.edu/~gohlke/pythonlibs/#pycairo. For most users, ``pycairo‑1.18.0‑cp37‑cp37m‑win32.whl`` will do fine. ``sh pip3 install C:\path\to\wheel\pycairo‑1.18.0‑cp37‑cp37m‑win32.whl``
3. Install a LaTeX distribution -- MiKTeX https://miktex.org/download -- is recommended.
4. Install SoX: https://sourceforge.net/projects/sox/files/sox/

* **Mac**

The simplest way to install the system dependencies on Mac OS X is with Homebrew.
1. Installing Cairo: `` brew install cairo `` 
2. Installing Sox: ``brew install sox``
3. Installing ffmpeg: `` brew install ffmpeg ``
4. Installing latex (MiKTeX): https://miktex.org/howto/install-miktex-mac 



Installation via Docker
-----------
Since it's a bit tricky to get all the dependencies set up just right, there is a Dockerfile and Compose file provided in this repo as well as `a premade image on Docker Hub
<https://hub.docker.com/r/eulertour/manim/tags/>`_. The Dockerfile contains instructions on how to build a manim image, while the Compose file contains instructions on how to run the image.

The image does not contain a copy of the repo. This is intentional, as it allows you to either bind mount a repo that you've cloned locally or clone any fork/branch you want. In order to do this with the Compose file, you must set the `MANIM_PATH` environment variable to the absolute path to the manim repo.

1. Install Docker: https://www.docker.com/products/overview
2. Install Docker (Compose) : https://docs.docker.com/compose/install/
3. Render an animation

```sh
MANIM_PATH=/absolute/path/to/manim/repo docker-compose run manim example_scenes.py SquareToCircle -l
```

The first time you execute the above command, Docker will pull the image from Docker Hub and cache it. Any subsequent runs until the image is evicted will use the cached image.
Note that the image doesn't have any development tools installed and can't preview animations. Its purpose is building and testing only.


Installing manim repository
-----------
If you want to hack on manimlib itself, clone `Grant Sanderson's git repository <https://github.com/3b1b/manim>`_. and run ``python3 -m pip install -r requirements.txt``. Note that you'll have to add manim's folder to **pythonpath** in order to run your animations from any other folder.
