# React Native

Lets get started with the tutorial on React Native.

### First Step: Installation and Building a new react native application.

**Reference:**
[Installation process](https://facebook.github.io/react-native/docs/getting-started)

Choose the **(Building Projects with Native Code)** Option. (I have chosen Windows Installation.)
As we are going to use Android Studio instead of Expo. Expo is the easiest way to start building a new React Native application.
But it has some restrictions which is overcomed by Android Studio. Expo works best for beginners.

**Installation Process:**
You will need Node, the React Native command line interface, Python2, a JDK, and Android Studio.
For Windows:
1. [Download and Install Nodejs](https://nodejs.org/en/download/)
2. [Install npm]()
```
npm install npm@latest -g
```
3. Check Version (Node and npm) in Command Line Interface (run Command Prompt): 
```
node -v
```
```
npm -v
```
4. Now Install Python Latest version. [Download Link](https://www.python.org/downloads/)
Download the latest version for Windows (Python 3.7.2)
then check version on command prompt: 
```
python --version
```
5. The React Native CLI
Node comes with npm, which helps you install the React Native command line interface.
Run the following command in a Command Prompt or shell:
```
npm install -g react-native-cli
```

6. 
  - **Android Studio:** [Download Link](https://developer.android.com/studio/)
    Latest Version available: 3.3.1 for Windows 64-bit (947 MB).

    Make sure the boxes next to all of the following are checked:
    - Android SDK
    - Android SDK Platform
    - Performance (Intel ® HAXM) (See here for AMD)
    - Android Virtual Device
    - Then, click "Next" to install all of these components.

  - **Install the Android SDK:** Requires the **Android 9 (Pie) SDK** to install.
    > The Android Studio has **"Preferences"** option where Android SDK is found, under **Appearance & Behavior → System Settings → Android SDK**.
  - **Configuration (ANDROID_HOME environment variable):**
```
C:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk
```
1. The Windows Control Panel has a search bar, Search for the System.
2. Then click the option (Edit the system environment variables).
3. Click on Environment Variables
4. Click on New (In the User Variables or Add to both Sytem Variables as well.)
5. Add platform-tools to Path
Select the Path variable, then click Edit. Copy and Paste this given command with your **PC Username**
```
C:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk\platform-tools
```
Now we are ready to go and develop our application.

### Creating a new application
Using the React Native command line interface to start a new React Native project called **"AwesomeProject"**:
```
react-native init AwesomeProject
```
Preparing the Android device
There are two methods to run an application on device.
1. Using a physical device
2. Using a virtual device

I am using Android device (physical) connected through USB debugging. Make sure Developer Option in settings is visible.
To follow instructions on how to connect: Here is the link -> [Running your app on Android devices](https://facebook.github.io/react-native/docs/running-on-device)

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/pic1.png)
![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/pic2.png)
**Running your React Native application**
**Note:** Run (react-native run-android) inside your project folder:
```
cd AwesomeProject
react-native run-android
```

If everything is set up and working correctly, you should see your new app running in your Android device.



