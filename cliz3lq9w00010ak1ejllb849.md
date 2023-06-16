---
title: "React Native Installation Guide on Windows"
datePublished: Fri Jun 16 2023 21:44:56 GMT+0000 (Coordinated Universal Time)
cuid: cliz3lq9w00010ak1ejllb849
slug: react-native-installation-guide-on-windows
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686951614976/61602747-4f59-444a-ba78-1e714edd27b5.png
tags: react-native, windows, reactjs, guide, installation

---

React Native is a popular framework for building cross-platform mobile applications using JavaScript and React. In this tutorial, we will guide you through the process of setting up React Native on a Windows device using Chocolatey package manager. We will also show you how to initialize a new React Native project after installation.

## Prerequisites

Before we begin, make sure your Windows device meets the following requirements:

* Windows 7 or later (64-bit)
    
* Node.js (version 8 or later)
    
* JDK (version 8 or later)
    
* Android Studio (version 3.0 or later) with Android SDK and Android Virtual Device (AVD) installed
    

## Step 1: Install Chocolatey

Chocolatey is a package manager for Windows that makes it easy to install and manage software packages. To install Chocolatey, open PowerShell as an administrator and run the following command:

```solidity
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

This command will download and install Chocolatey on your Windows device.

If this does not work, then you can use this also

```solidity
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## Step 2: Install React Native CLI

After installing Chocolatey, open PowerShell as an administrator and run the following command to install the React Native CLI:

```solidity
choco install -y nodejs-lts microsoft-openjdk11
```

This command will install Node.js, Python 2, JDK 8, and the React Native CLI on your Windows device.

## Extra :- Download and Install Android Studio

#### 1\. Install Android Studio[​](https://reactnative.dev/docs/environment-setup#android-studio)

[Download and install Android Studio](https://developer.android.com/studio/index.html). While on Android Studio installation wizard, make sure the boxes next to all of the following items are checked:

* `Android SDK`
    
* `Android SDK Platform`
    
* `Android Virtual Device`
    
* If you are not already using Hyper-V: `Performance (Intel ® HAXM)` ([See here for AMD or Hyper-V](https://android-developers.googleblog.com/2018/07/android-emulator-amd-processor-hyper-v.html))
    

Then, click "Next" to install all of these components.

> If the checkboxes are grayed out, you will have a chance to install these components later on.

Once setup has finalized and you're presented with the Welcome screen, proceed to the next step.

#### 2\. Install the Android SDK[​](https://reactnative.dev/docs/environment-setup#android-sdk)

Android Studio installs the latest Android SDK by default. Building a React Native app with native code, however, requires the `Android 13 (Tiramisu)` SDK in particular. Additional Android SDKs can be installed through the SDK Manager in Android Studio.

To do that, open Android Studio, click on "More Actions" button and select "SDK Manager".

![Android Studio Welcome](https://reactnative.dev/assets/images/GettingStartedAndroidStudioWelcomeWindows-ce20d1230828a1a26e143e3a4145f1df.png align="left")

> The SDK Manager can also be found within the Android Studio "Preferences" dialog, under **Appearance & Behavior** → **System Settings** → **Android SDK**.

Select the "SDK Platforms" tab from within the SDK Manager, then check the box next to "Show Package Details" in the bottom right corner. Look for and expand the `Android 13 (Tiramisu)` entry, then make sure the following items are checked:

* `Android SDK Platform 33`
    
* `Intel x86 Atom_64 System Image` or `Google APIs Intel x86 Atom System Image`
    

Next, select the "SDK Tools" tab and check the box next to "Show Package Details" here as well. Look for and expand the `Android SDK Build-Tools` entry, then make sure that `33.0.0` is selected.

Finally, click "Apply" to download and install the Android SDK and related build tools.

#### 3\. Configure the ANDROID\_HOME environment variable

The React Native tools require some environment variables to be set up in order to build apps with native code.

1. Open the **Windows Control Panel.**
    
2. Click on **User Accounts,** then click **User Accounts** again
    
3. Click on **Change my environment variables**
    
4. Click on **New...** to create a new `ANDROID_HOME` user variable that points to the path to your Android SDK:
    

![ANDROID_HOME Environment Variable](data:image/png;base64,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 align="left")

The SDK is installed, by default, at the following location:

```solidity
%LOCALAPPDATA%\Android\Sdk
```

You can find the actual location of the SDK in the Android Studio "Settings" dialog, under **Appearance & Behavior** → **System Settings** → **Android SDK**.

Open a new Command Prompt window to ensure the new environment variable is loaded before proceeding to the next step.

1. Open powershell
    
2. Copy and paste **Get-ChildItem -Path Env:\\** into powershell
    
3. Verify `ANDROID_HOME` has been added
    

#### 4\. Add platform-tools to Path

1. Open the **Windows Control Panel.**
    
2. Click on **User Accounts,** then click **User Accounts** again
    
3. Click on **Change my environment variables**
    
4. Select the **Path** variable.
    
5. Click **Edit.**
    
6. Click **New** and add the path to platform-tools to the list.
    

The default location for this folder is:

```solidity
%LOCALAPPDATA%\Android\Sdk\platform-tools
```

### React Native Command Line Interface

React Native has a built-in command line interface. Rather than install and manage a specific version of the CLI globally, we recommend you access the current version at runtime using `npx`, which ships with Node.js. With `npx react-native <command>`, the current stable version of the CLI will be downloaded and executed at the time the command is run.

## Creating a new application

> If you previously installed a global `react-native-cli` package, please remove it as it may cause unexpected issues:
> 
> ```solidity
> npm uninstall -g react-native-cli @react-native-community/cli
> ```

React Native has a built-in command line interface, which you can use to generate a new project. You can access it without installing anything globally using `npx`, which ships with Node.js. Let's create a new React Native project called "AwesomeProject":

```solidity
npx react-native@latest init AwesomeProject
```

This is not necessary if you are integrating React Native into an existing application, if you "ejected" from Expo, or if you're adding Android support to an existing React Native project (see [Integration with Existing Apps](https://reactnative.dev/docs/integration-with-existing-apps)). You can also use a third-party CLI to init your React Native app, such as [Ignite CLI](https://github.com/infinitered/ignite).

### \[Optional\] Using a specific version or template

If you want to start a new project with a specific React Native version, you can use the `--version` argument:

```solidity
npx react-native@X.XX.X init AwesomeProject --version X.XX.X
```

You can also start a project with a custom React Native template with the `--template` argument.

## Preparing the Android device

You will need an Android device to run your React Native Android app. This can be either a physical Android device, or more commonly, you can use an Android Virtual Device which allows you to emulate an Android device on your computer.

Either way, you will need to prepare the device to run Android apps for development.

### Using a physical device

If you have a physical Android device, you can use it for development in place of an AVD by plugging it in to your computer using a USB cable and following the instructions [here](https://reactnative.dev/docs/running-on-device).

### Using a virtual device

If you use Android Studio to open `./AwesomeProject/android`, you can see the list of available Android Virtual Devices (AVDs) by opening the "AVD Manager" from within Android Studio. Look for an icon that looks like this:

![Android Studio AVD Manager](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB0AAAAZCAIAAABCYLJOAAACLUlEQVR4Ab2Vw6IfPxiG3zfJHPPP2rbdfW3rProsLqCr7rqsbVur2raPPb+Z5Du2+YyRJ87HtLQ0dAIKnYNBQ5BEI4hI271BEIjUNZAgqbUm2WovyRLpyVMnfd83xggq3ATDMHTOzZo1q3ev3iRbXV4RKZEuXLBQayPOAQSESjlnDx85nJ+fjwpa7zUlaHPj2CO/oLTUNnTR8Wb2kvGeZ9rVbwJxTuArm69haAMaqtJXgnZ5y1tVmxKsMoqgKS0p2z1+WdEgItWXjp4XJEiCHesVZ50LnbUOrcE0LQURk2BsYHU0ASmnuqUgrfaSEAcvWs9eMQbKGe0J0L17j8TERJICW+hnx0Ylk6o17SAVF6U1lL3/bld+UbrAzpgx9f///4sEeT/TH955srMwkk2wNeUlROCsiBNCicu7dH+zH5BUgChapThh0NrYqCRpbTsoxZiEKBu60EbSsr+m5Z7RaoiIJQkQkv3lz8De/8/0tJEWekmKdSXb9MUjRYK7L3bk+996/7PpT/Zr6yIko0xcSsK0r2n33/+4NLjnXNIA0nz7kizy/b379ly6ckGIb+kPUhP7zZu5zTN/B/ZzaL+lxPecN2O7YsKbL2edOLLF5f3/v/+zsrOSk1MAxEb1z8j5dezaVggTYiYDyCnIP359q4gENl4EDdJwfLPWAiCplAptABEHp2oMKSfljzTaa0W/GVPxXkQ8EwWw5gCs+VhCK7w1/25o0ZHOj8dd7C0GRnwgNA5r8rwAAAAASUVORK5CYII= align="left")

If you have recently installed Android Studio, you will likely need to [create a new AVD](https://developer.android.com/studio/run/managing-avds.html). Select "Create Virtual Device...", then pick any Phone from the list and click "Next", then select the **Tiramisu** API Level 33 image.

> If you don't have HAXM installed, click on "Install HAXM" or follow [these instructions](https://github.com/intel/haxm/wiki/Installation-Instructions-on-Windows) to set it up, then go back to the AVD Manager.

Click "Next" then "Finish" to create your AVD. At this point you should be able to click on the green triangle button next to your AVD to launch it, then proceed to the next step.

## Step 3: Initialize a New React Native Project

After installing the React Native CLI, you can initialize a new React Native project by running the following command:

```solidity
npx react-native@latest init AwesomeProject
```

Replace "MyProject" with the name of your project. This command will create a new React Native project with the specified name in the current directory.

## Step 4: Run the React Native App

To run the React Native app, open PowerShell as an administrator and navigate to the project directory by running the following command:

```solidity
cd AwesomeProject
```

Replace "MyProject" with the name of your project. This command will change the current directory to your project directory.

Next, start the development server by running the following command:

```solidity
npx react-native start
```

This command will start the development server for your React Native app.

Finally, open another PowerShell window as an administrator and run the following command to launch the app in the Android emulator:

```solidity
npx react-native run-android
```

This command will launch the app in the Android emulator.

Congratulations! You have successfully set up React Native on your Windows device and created a new React Native project. You can now start building your own cross-platform mobile apps using React Native.