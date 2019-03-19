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
react-native init Sagarkalyan
```
Preparing the Android device
There are two methods to run an application on device.
1. Using a physical device
2. Using a virtual device

I am using Android device (physical) connected through USB debugging. Make sure Developer Option in settings is visible.
To follow instructions on how to connect: Here is the link -> [Running your app on Android devices](https://facebook.github.io/react-native/docs/running-on-device)

**Running your React Native application**
**Note:** Run (react-native run-android) inside your project folder:
```
cd Sagarkalyan
react-native run-android
```
![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/pic2.png)

If everything is set up and working correctly, you should see your new app running in your Android device.

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/pic3-1.jpg)



### Second Step: Start Coding for a new react native application.


# We will start Coding in App.js (root folder of Project [Sagarkalyan])
## 1. Remove Code
Removing Some specific code which is by default given when we run the application for the first time.

```html
const instructions = Platform.select({
  ios: 'Press Cmd+R to reload,\n' + 'Cmd+D or shake for dev menu',
  android:
    'Double tap R on your keyboard to reload,\n' +
    'Shake or press menu button for dev menu',
});

type Props = {};
export default class App extends Component<Props> {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>Welcome to React Native!</Text>
        <Text style={styles.instructions}>To get started, edit App.js</Text>
        <Text style={styles.instructions}>{instructions}</Text>
      </View>
    );
  }
}
const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  instructions: {
    textAlign: 'center',
    color: '#333333',
    marginBottom: 5,
  },
});
  
```

## 2. Navigating Between Screens

The first step is to install in your project:

Install the react-navigation package in your React Native project.
**Use Command line -**
```
npm install --save react-navigation
```

Next, install react-native-gesture-handler.
**Use Command line -**
```
npm install --save react-native-gesture-handler@~1.0.14
```

Link all native dependencies:
**Use Command line -**
```
react-native link react-native-gesture-handler
```

Now, Final Step of installation of react-native-gesture-handler for Android,
be sure to make the necessary modifications to **MainActivity.java:**
**Android/app/src/main/java/com/sagarkalyan/MainActivity.java**

```
package com.sagarkalyan;

import com.facebook.react.ReactActivity;

import com.facebook.react.ReactActivityDelegate;
import com.facebook.react.ReactRootView;
import com.swmansion.gesturehandler.react.RNGestureHandlerEnabledRootView;

public class MainActivity extends ReactActivity {

    /**
     * Returns the name of the main component registered from JavaScript.
     * This is used to schedule rendering of the component.
     */
    @Override
    protected String getMainComponentName() {
        return "Sagarkalyan";
    }

    @Override
    protected ReactActivityDelegate createReactActivityDelegate() {
        return new ReactActivityDelegate(this, getMainComponentName()) {
        @Override
        protected ReactRootView createRootView() {
            return new RNGestureHandlerEnabledRootView(MainActivity.this);
      }
    };
    }
}
```


We are going to make two navigating screens and navigate them through Buttons.

Then,add the folowing code in App.js
**In App.js -**
```

import React, {Component} from 'react';
import {Platform, StyleSheet, Text, View, Button } from 'react-native';
import { createStackNavigator, createAppContainer } from "react-navigation";


class HomeScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
         <Text>Hi, Welcome to Creators App!</Text>
        <Button
            title="About Me"
            onPress={() => this.props.navigation.navigate('AboutMe')}
            />
      </View>
    );
  }
}

// This is second page. (About me)
class DetailsScreen extends React.Component {
  render() {
    return (
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
        <Text>About Me</Text>
        <Button title="Back to Home" onPress={() => this.props.navigation.navigate('Home')} />
      </View>
    );
  }
}

const AppNavigator = createStackNavigator(
  {
    Home: HomeScreen,
    AboutMe: DetailsScreen
  },
  {
    initialRouteName: "Home"
  }
);
export default createAppContainer(AppNavigator);
```

If you run this code, you will see a screen with an empty navigation bar and a white content area containing your HomeScreen component.
```
react-native run-android
```

Now our stack has two routes, a Home route and a AboutMe route. The Home route corresponds to the HomeScreen component, and the AboutMe route corresponds to the DetailsScreen component.






