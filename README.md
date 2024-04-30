# esp-drone PC client 

The esp-drone PC client is a fork of the [Crazyflie PC client](./ORIGIN.md). The communication with esp-drone and the implementation of the CRTP protocol to control the esp-drone is handled by the modified [cflib](https://github.com/leeebo/crazyflie-lib-python)

# Running from source

The client requires the folked [cflib](https://github.com/leeebo/crazyflie-lib-python).
If you want to develop with the lib too, follow the cflib readme to install it.

## Windows (10/11)

Running from source on Windows is tested using the official python build from [python.org](https://python.org). The client works with **python version >= 3.5 and <= 3.10**. The procedure is tested with 32bit python. It should work with 64bit python but since it is not tested it can be broken (if so, do not hesitate to send a fix ;-).

To run the client you should install python, make sure to check the "add to path" checkbox during install. You should also have git installed and in your path. Use git to clone the client project.

Open a command line window and move to the clients folder (the exact command depends of where the project is cloned)

```
cd crazyflie-clients-python
```

Download the SDL2.dll Windows library:

```
python tools\build\prep_windows
```

Install the client in development mode:

```
pip install -e .[dev,qt5]
```

You can now run the clients with the `cfclient` commands:

### Creating Windows installer

When you are able to run from source, you can build the windows executable and installer.

First build the executable

```
python setup.py build
```

Now you can run the client with ```build\exe.win32-3.6\cfclient.exe```.

To generate the installer you need [nsis](http://nsis.sourceforge.net/) installed and in the path. If you
are a user of [chocolatey](https://chocolatey.org/) you can install it with ```choco install nsis.portable -version 2.50```,
otherwise you can just download it and install it manually.

To create the installer:
```
python win32install\generate_nsis.py
makensis win32install\cfclient.nsi
```


### Dependencies

The Crazyflie PC client has the following dependencies:

* Installed from system packages
  * Python 3.4+ and <= 3.10
  * PyQt5
  * A pyusb backend: libusb 0.X/1.X
* Installed from PyPI using PIP:
  * cflib (pip install git+https://github.com/leeebo/crazyflie-lib-python.git)
  * PyUSB
  * PyQtGraph
  * ZMQ
  * appdirs
  * PyYAML
