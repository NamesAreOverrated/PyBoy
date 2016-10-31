# PyBoy

It is highly recommended to read the [report](https://github.com/Baekalfen/PyBoy/raw/master/PyBoy.pdf) to get a light introduction to Game Boy emulation. The report is relevant, eventhough you want to contribute to another emulator, or create your own.

If you've read the report and want more explicit details, have a look at the [Pan Docs](http://bgb.bircd.org/pandocs.htm).

Abstract
========
This project is covering an emulation of the Nintendo Game Boy (DMG-01) from 1989. The Game Boy has been emulated many times before, but this project will emulate it in the programming language Python 2.7. The implementation is not based on any existing emulator, but is made from scratch. The emulation has proven to be fast enough, to run software from cartridge dumps, with the same speed as the Game Boy. Most essential components of the Game Boy, are part of the emulation, but sound and serial port are not included in this project. The implementation runs in almost pure Python, but with dependencies for drawing graphics and getting user interactions through SDL2 and NumPy.

![alt tag](https://github.com/Baekalfen/PyBoy/raw/master/README/1.png)
![alt tag](https://github.com/Baekalfen/PyBoy/raw/master/README/2.png)
![alt tag](https://github.com/Baekalfen/PyBoy/raw/master/README/3.png)
![alt tag](https://github.com/Baekalfen/PyBoy/raw/master/README/4.png)
![alt tag](https://github.com/Baekalfen/PyBoy/raw/master/README/5.png)

Starting the Emulator
=====================
It should be noted, that the emulator is not ready for use, and is still in development.

CPython is no where fast enough to run the emulator (see [Report.pdf](https://github.com/Baekalfen/PyBoy/raw/master/PyBoy.pdf) about performance). It is therefore required to use PyPy.

The code has a few dependencies, but it should be fairly easy to get it up and running. The code developed on Mac OS X, but has been tested to run on Ubuntu 16.04.

macOS
-----
The easiest way to get started, is to first install [brew](https://www.brew.sh).

When brew is installed, the depencencies can be installed with the following five commands in the terminal:

    brew update
    brew install pypy sdl2
    brew link sdl2
    brew install sdl2 sdl2_gfx sdl2_image
    pip_pypy install git+https://bitbucket.org/pypy/numpy.git
    hg clone https://bitbucket.org/marcusva/py-sdl2 && cd py-sdl2/ && pypy setup.py install

Ubuntu/Linux
------------
Ubuntu some problems installing PyPy in parallel with the system version of CPython. Therefore, we will install the PyPy version of NumPy in a virtualenv.

Git and Mercurial is not strictly needed for the emulator. You can choose not to install them, if you download and install PySDL2 and NumPy manually.

    sudo apt update
    sudo apt install git mercurial
    sudo apt install pypy pypy-dev virtualenv libsdl2-dev

Now move to the `PyBoy/Source` directory before creating the virtual environment:

    virtualenv . -p `which pypy`
    source ./bin/activate

    pip install git+https://bitbucket.org/pypy/numpy.git

    hg clone https://bitbucket.org/marcusva/py-sdl2
    cd py-sdl2/
    pypy setup.py install
    cd ..
    rm -rf py-sdl2/

Setup and Run
-------------
Now, create a directory at `Source/ROMs` and place your ROMs in this directory -- which you of course dumped yourself with [PyBoyCartridge](https://github.com/Baekalfen/PyBoyCartridge)

Then run `pypy main.py` from the `Source` directory and choose a ROM to start.

License
=======
Creative Commons BY-NC-SA 4.0
http://creativecommons.org/licenses/by-nc-sa/4.0/

