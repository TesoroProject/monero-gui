# Tesoro GUI

Copyright (c) 2014-2019 The Monero Project.

Copyright (c) 2019-2020 TesoroDev.

Portions Copyright (c) 2012-2013 The Cryptonote developers.

## Development resources

- Web: [getmonero.org](https://tesoro.dev/)
- Mail: [dev@getmonero.org](mailto:tesorocurrency@gmail.com)
- Github: [https://github.com/tesoro-project/tesoro-gui](https://github.com/tesoro-dev/tesoro-gui)
- IRC: [#tesoro-dev on Freenode](irc://chat.freenode.net/#tesoro-dev)
- UI Design: [Monero-GUI on Figma](https://www.figma.com/file/DplJ2DDQfIKiuRvolHX2hN/Monero-GUI)

## About this project

Tesoro (TSX) is  a  decentralized  cryptocurrency  based  on  PoW  consensus  that  uses  RandomX algorithm which favours CPU powered PCs over GPUs allowing average users to be a part of the creation and maintenance of its blockchain and network and also using modified Monero source code in Tesoro grants compatibility along with high security and privacy features. TesoroDev was  initiated as a  group  of  independent  of  developers spread  out  through many different countries to develop the Tesoro (TSX) cryptocurrency.

## License

See [LICENSE](LICENSE).

## Installing the Tesoro GUI from a package

Packages are available for

* Arch Linux: pacman -S tesoro-gui
* Void Linux: xbps-install -S tesoro-core
* GuixSD: guix package -i tesoro-core

Packaging for your favorite distribution would be a welcome contribution!

## Compiling the Tesoro GUI from source

*Note*: Qt 5.9.7 is the minimum version required to build the GUI.

### On Linux:

(Tested on Ubuntu 17.10 x64, Ubuntu 18.04 x64 and Gentoo x64)

1. Install Tesoro dependencies

  - For Debian distributions (Debian, Ubuntu, Mint, Tails...)

	`sudo apt install build-essential cmake libboost-all-dev miniupnpc libunbound-dev graphviz doxygen libunwind8-dev pkg-config libssl-dev libzmq3-dev libsodium-dev libhidapi-dev libnorm-dev libusb-1.0-0-dev libpgm-dev`

  - For Gentoo

	`sudo emerge app-arch/xz-utils app-doc/doxygen dev-cpp/gtest dev-libs/boost dev-libs/expat dev-libs/openssl dev-util/cmake media-gfx/graphviz net-dns/unbound net-libs/ldns net-libs/miniupnpc net-libs/zeromq sys-libs/libunwind dev-libs/libsodium dev-libs/hidapi`

  - For Fedora

	`sudo dnf install make automake cmake gcc-c++ boost-devel miniupnpc-devel graphviz doxygen unbound-devel libunwind-devel pkgconfig openssl-devel libcurl-devel hidapi-devel libusb-devel zeromq-devel`

2. Install Qt:

  *Note*: The Qt 5.9.7 or newer requirement makes **some** distributions (mostly based on debian, like Ubuntu 16.x or Linux Mint 18.x) obsolete due to their repositories containing an older Qt version.

 The recommended way is to install 5.9.7 from the [official Qt installer](https://www.qt.io/download-qt-installer) or [compiling it yourself](https://wiki.qt.io/Install_Qt_5_on_Ubuntu). This ensures you have the correct version. Higher versions *can* work but as it differs from our production build target, slight differences may occur.

The following instructions will fetch Qt from your distribution's repositories instead. Take note of what version it installs. Your mileage may vary.

  - For Ubuntu 17.10+

    `sudo apt install qtbase5-dev qt5-default qtdeclarative5-dev qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs qml-module-qtquick-xmllistmodel qml-module-qt-labs-settings qml-module-qt-labs-folderlistmodel qttools5-dev-tools qml-module-qtquick-templates2 libqt5svg5-dev`

  - For Gentoo

    `sudo emerge dev-qt/qtcore:5 dev-qt/qtdeclarative:5 dev-qt/qtquickcontrols:5 dev-qt/qtquickcontrols2:5 dev-qt/qtgraphicaleffects:5`

  - Optional : To build the flag `WITH_SCANNER`

    - For Ubuntu

      `sudo apt install qtmultimedia5-dev qml-module-qtmultimedia libzbar-dev`

    - For Gentoo

      The *qml* USE flag must be enabled.

      `emerge dev-qt/qtmultimedia:5 media-gfx/zbar`


3. Clone repository

    `git clone https://github.com/tesoro-dev/tesoro-gui.git`

4. Build

    ```
    cd tesoro-gui
    QT_SELECT=5 ./build.sh
    ```

The executable can be found in the build/release/bin folder.

### On OS X:

1. Install Xcode from AppStore

2. Install [homebrew](http://brew.sh/)

3. Install [tesoro](https://github.com/tesoro-dev/tesoro) dependencies:

  `brew install boost`

  `brew install openssl` - to install openssl headers

  `brew install pkgconfig`

  `brew install cmake`

  `brew install zeromq`

  *Note*: If cmake can not find zmq.hpp file on OS X, installing `zmq.hpp` from https://github.com/zeromq/cppzmq to `/usr/local/include` should fix that error.

4. Install Qt:

  `brew install qt5`  (or download QT 5.9.7+ from [qt.io](https://www.qt.io/download-open-source/))

  If you have an older version of Qt installed via homebrew, you can force it to use 5.x like so:
  
  `brew link --force --overwrite qt5`

5. Add the Qt bin directory to your path

  - Example for Qt: `export PATH=$PATH:$HOME/Qt/5.9.7/clang_64/bin`
  - Example for Homebrew: `export PATH=$PATH:/usr/local/opt/qt/bin`

6. Grab an up-to-date copy of the tesoro-gui repository

  `git clone https://github.com/tesoro-dev/tesoro-gui.git`

7. Go into the repository

  `cd tesoro-gui`

8. Start the build

  `./build.sh`

The executable can be found in the `build/release/bin` folder.

**Note:** Workaround for "ERROR: Xcode not set up properly"

Edit `$HOME/Qt/5.9.7/clang_64/mkspecs/features/mac/default_pre.prf`

replace
`isEmpty($$list($$system("/usr/bin/xcrun -find xcrun 2>/dev/null")))`

with
`isEmpty($$list($$system("/usr/bin/xcrun -find xcodebuild 2>/dev/null")))`

More info: http://stackoverflow.com/a/35098040/1683164


### On Windows:

The Tesoro GUI on Windows is 64 bits only.

1. Install [MSYS2](https://www.msys2.org/), follow the instructions on that page on how to update system and packages to the latest versions

2. Open an 64-bit MSYS2 shell: Use the *MSYS2 MinGW 64-bit* shortcut, or use the `msys2_shell.cmd` batch file with a `-mingw64` parameter

3. Install MSYS2 packages for Tesoro dependencies; the needed 64-bit packages have `x86_64` in their names

    ```
    pacman -S mingw-w64-x86_64-toolchain make mingw-w64-x86_64-cmake mingw-w64-x86_64-boost mingw-w64-x86_64-openssl mingw-w64-x86_64-zeromq mingw-w64-x86_64-libsodium mingw-w64-x86_64-hidapi mingw-w64-x86_64-protobuf-c mingw-w64-x86_64-libusb
    ```

    Optional : To build the flag `WITH_SCANNER`

      ```
      pacman -S mingw-w64-x86_64-zbar
      ```

    You find more details about those dependencies in the [Tesoro documentation](https://github.com/tesoro-dev/tesoro). Note that that there is no more need to compile Boost from source; like everything else, you can install it now with a MSYS2 package.

4. Install Qt5

    ```
    pacman -S mingw-w64-x86_64-qt5
    ```

    There is no more need to download some special installer from the Qt website, the standard MSYS2 package for Qt will do in almost all circumstances.

5. Install git

    ```
    pacman -S git
    ```

6. Clone repository

    ```
    git clone https://github.com/tesoro-dev/tesoro-gui.git
    ```

7. Build

    ```
    cd tesoro-gui
    source ./build.sh release-static
    cd build
    make deploy
    ```

    **Note:** The use of `source` above is a dirty workaround for a suspected bug in the current QT version 5.11.2-3 available in the MSYS2 packaging system, see https://github.com/tesoro-dev/tesoro-gui/issues/1559 for more info.

The executable can be found in the `.\release\bin` directory.
