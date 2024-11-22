# [macOS] Install CMake

ref : https://gist.github.com/fscm/29fd23093221cf4d96ccfaac5a1a5c90

Instructions on how to install the CMake tool on macOS.

## Uninstall

First step should be to unsinstall any previous CMake installation. This step 
can be skipped if no CMake version was previously installed.

To uninstall any previous CMake installations use the following commands:

```sh
sudo find /usr/local/bin -type l -lname '/Applications/CMake.app/*' -delete
sudo rm -rf /Applications/CMake.app
```

## Install

The CMake tool can be obtained [here](https://cmake.org/download/). 
Copy the link for the package version that you want to install from there.

Get the CMake installer package using the following commands:

```sh
mkdir ~/Downloads/CMake
curl --silent --location --retry 3 "https://github.com/Kitware/CMake/releases/download/v3.28.3/cmake-3.28.3-macos-universal.dmg" --output ~/Downloads/CMake/cmake-macos.dmg
```

Mount the image using the following command:
```sh
yes | PAGER=cat hdiutil attach -quiet -mountpoint /Volumes/cmake-macos ~/Downloads/CMake/cmake-macos.dmg
```

Copy the CMake app to the applications folder using the following command:
```sh
cp -R /Volumes/cmake-macos/CMake.app /Applications/
```

Unmount the image using the following command:
```sh
hdiutil detach /Volumes/cmake-macos
```

Add the CMake tool to the PATH using the following command:
```sh
sudo "/Applications/CMake.app/Contents/bin/cmake-gui" --install=/usr/local/bin
```

## Verify

Open a new terminal window and check if the CMake tool is installed:

```sh
cmake --version
```

## Clean up

After installing the CMake tool you can remove the downloaded installation 
image using the following command:

```sh
rm -rf ~/Downloads/CMake
```
