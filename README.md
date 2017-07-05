Step :

- An unlimited internet connection (This is huge, especially the Android SDK size itself need about 8GB)
- [Java JDK](#install-java-jdk)
- [Android SDK](#install-android-sdk)
- [NodeJS (via NVM)](#install-node)
- [Appium Server](#appium)
- [Python (2.7.x) + pip](#python-and-pip)
- [Configure the requirements.txt + Installation using pip](#install-requirements-using-pip)

## Install Java JDK

First, we need to make sure that OpenJDK isn't installed on ubuntu. To make sure, run this command from terminal

```
$ java -version
```

It will show something like this if OpenJDK installed on your system:

```
java version "1.7.0_15"
OpenJDK Runtime Environment (IcedTea6 1.10pre) (7b15~pre1-0lucid1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
```

But if it Java JDK, it will show something like this:

```
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
```

Then you're safe to continue to next step. If not, run this command to purge all OpenJDK from system:

```
$ sudo apt-get purge openjdk-\*
```

Type Y then enter if asked.

After that, let's add java jdk repository for ubuntu with this command:

```
$ sudo add-apt-repository ppa:webupd8team/java && sudo apt-get update
```

Then install java jdk using this command:

```
$ sudo apt-get install oracle-java8-installer
```

Run this command again after installation is finished, to make sure java is successfully installed:

```
$ java -version
```

System will output something like this:

```
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
```

## Install Android SDK

Run this command to download Android SDK (will be located on your /home/your_user_folder)

```
$ cd ~
$ wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip?hl=id
```

Wait until the process is finished.

Next, run this command to extract the Android SDK that we already downloaded

```
$ cd ~
$ uzip sdk-tools-linux-3859397.zip
```

Then, we need to configure ~/.bashrc file, so we can using android sdk command from anywhere. Also we need to set the JAVA_HOME path too. Edit .bashrc using your favourite editor:

```
$ nano ~/.bashrc
```

Move to end of the file, then add this line:

```
export ANDROID_HOME=$HOME/android-sdk-linux
export ANDROID_SDK=$ANDROID_HOME
PATH=$PATH:$ANDROID_HOME/build-tools
PATH=$PATH:$ANDROID_HOME/platform-tools
PATH=$PATH:$ANDROID_HOME/tools
export JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
export PATH=$JAVA_HOME/jre/bin:$PATH

export PATH
```

Save the file, then run source command:

```
$ source ~/.bashrc
```

Then, run this command to open the Android SDK Manager:

```
$ android
```

On this window, we need to tick several packages that appium need to run:

> Tools

v Android SDK Tools (Latest)

v Android SDK Platform-tool (Latest)

v Android SDK Build-tools (Latest)

> Android 6.0 (API 23)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Google APIs Intel x86 Atom System Image

> Android 5.1.1 (API 22)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Google APIs Intel x86 Atom System Image

> Android 5.0.1 (API 21)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Google APIs Intel x86 Atom System Image

> Android 4.4.2 (API 19)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Google APIs Intel x86 Atom System Image

> Android 4.3.1 (API 18)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Intel x86 Atom System Image

> Android 4.2.2 (API 17)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Intel x86 Atom System Image

> Android 4.1.2 (API 16)

v SDK Platform

v Google APIs

v [Optional, if you want to using emulator] Intel x86 Atom System Image

> Extras

v Android Support Repository

v Google Play Services

v Google Web Driver

Click Install Packages, Accept License, and wait until installation finished

## Install Node

For simplicity and modularity, we will use NVM (Node Version Manager). You may want to remove the default nodejs from ubuntu repository, although it will not conflict with nvm because it will create different directory.

Download and install nvm (you can check the latest version [here](https://github.com/creationix/nvm))

```
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.4/install.sh | bash
```

Restart the terminal, then run this command to start installing nodejs using nvm:

```
$ nvm install 4.2.4
$ nvm alias default 4.2.4
```

From our experience, it is recommended to stick using LTS version.

## Appium

Now, let's install the appium with this command:

```
$ npm install -g grunt grunt-cli appium --verbose
```

Wait until installation finished. To make sure appium installed successfully, run this command:

```
$ appium
```

It will show something like this:

```
info: Welcome to Appium v1.4.16 (REV ae6877eff263066b26328d457bd285c0cc62430d)
info: Appium REST http interface listener started on 0.0.0.0:4723
info: Console LogLevel: debug
```

You can close it for now by pressing Ctrl+C

## Python And Pip

Python is needed for robot framework. Run this command to check your python version:

```
$ python -V
```

If it showing version 2.7.x, then you're safe. If it showing version 3, then you need to downgrade it to 2.7.x

Also, make sure pip is installed too. If not, you can refer [here](https://pip.pypa.io/en/stable/installing/) to installing pip.


## Install requirements using pip

Change directory to your project root

```
$ cd your_project_directory
```

Then run this command to start install the package needed to run robot framework

```
$ pip install -r requirements.txt
```

