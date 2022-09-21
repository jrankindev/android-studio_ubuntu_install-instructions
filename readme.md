# Android Studio Installation Instructions For Ubuntu 22.04.1 LTS
Note: This was only tested under Ubuntu 22.04.1 LTS with Android Studio 2021.3.1 but should work fine for any recent version of Ubuntu/Android Studio.

Contents:
+ [Prerequisites](#prerequisites)
+ [Android Studio Installation](#android-studio-installation)
+ [Android Debug Bridge Optional Installation](#android-debug-bridge---adb-optional)

---

## Prerequisites
Android Studio requires Java to be installed. First check if Java is installed:
```bash
java --version
```
The version should be JDK 11 or higher. If you have anything above 11 then skip to the "Android Studio Installation" section below.
If Java is not installed, install it:
```bash
sudo apt update && sudo apt install openjdk-11-jdk -y
```

---

## Android Studio Installation
First we need to add the official repository for Android Studio to Ubuntu:
```bash
sudo add-apt-repository ppa:maarten-fonville/android-studio -y
```

Now we can proceed to install Android Studio from the apt package manager:
```bash
sudo apt update && sudo apt install android-studio -y
```

Once Android Studio has finished installing, we need to launch it. You should be able to find Android Studio listed under your applications but if not, then run the start script to launch the application:
```bash
/opt/android-studio/bin/studio.sh
```

Now that Android Studio is running, we need to walk through the setup wizard.
1. Choose "Do not import settings".
2. Choose "Next" at the welcome screen.
3. Select "Standard" install type and then click "Next".
4. Select your preferred theme and then click "Next".
5. Click "Next" to verify settings.
6. Accept the terms and conditions and then click "Next".
7. Click "Finish". This will start the component downloads of the additional Android JDK and emulators.
8. Once the download is complete, click "Finish".
9. The "Welcome to Android Studio" dialog box will open, click "New Project".
10. Select "Basic Activity" and then click next.
11. Leave all the default settings and then click "Finish".
12. The Android SDK for your project will download now, click "Finish" when it completes.
13. Android Studio main window will now load. You will need to wait for the project setup to complete. You can see setup progress in the bottom right toolbar of the window.

You are now ready to use Android Studio with a virtual device (emulator). If you would like to setup a physical device proceed to the Android Debug Bridge section below.

---

## Android Debug Bridge - ADB (Optional)
First, add the current user to the 'plugdev' group:
```bash
sudo usermod -aG plugdev $LOGNAME
```
In order for the group changes to take effect, log out of Ubuntu and log back in or reboot your computer.

Now we can install ADB and tools:
```bash
sudo apt install android-sdk-platform-tools-common android-tools-adb -y
```

Now that ADB is installed, follow these instructions:
1. launch Android Studio and load into any project or start a new one.
2. Open the device manager window by choosing "Run -> Select Device..." from the top menu and then choosing "Device Manager".
3. Select the "Physical Device Tab".
4. Plug in your physical Android device (with USB debugging (Developer Mode/Options) already enabled) with a USB cable.
    - Note: If you need help with turning on Developer Mode/Options for your device, use Google to search for turning on developer mode for your specific version of Android.
5. A RSA ID message will pop-up on the phone screen, accept this message.

You are now ready to run Android Studio with the physical device you have plugged in.