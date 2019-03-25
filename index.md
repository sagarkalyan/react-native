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
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" &rbrace; }}>
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

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-1.jpg)

Now our stack has two routes, a Home route and a AboutMe route. The Home route corresponds to the HomeScreen component, and the AboutMe route corresponds to the DetailsScreen component.

**Some Basic Concept Understanding for Navigating to a new screen:**
1. **this.props.navigation:** the navigation prop is passed in to every screen component (definition) in stack navigator (more about this later in "The navigation prop in depth").
2. **navigate('Details'):** we call the navigate function (on the navigation prop — naming is hard!) with the name of the route that we'd like to move the user to.

For Understanding More About This part In Details: [React Navigation (Navigating to a new screen)](https://reactnavigation.org/docs/en/getting-started.html)


## 3. Adding Background Image on Home screen.
```
import {Platform, StyleSheet, Text, View, Button, ImageBackground } from 'react-native';

class HomeScreen extends React.Component {
  render() {
    return (
     <ImageBackground source={require('./app/img/bg_travel.jpeg')} style=\{{width: '100%', height: '100%'}}>
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
         <Text>Hi, Welcome to Creators App!</Text>
        <Button
            title="About Me"
            onPress={() => this.props.navigation.navigate('AboutMe')}
            />
      </View>
       </ImageBackground>
    );
  }
}
```
![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-2.jpg)

Modify the given above code, and then run your application again to check if its working properly. It will Show up the image in the background on Homepage screen.


## 4. Adding title on the top navigation bar,

```
class HomeScreen extends React.Component {
static navigationOptions = {
        title: 'Sagar Kalyan',
      };
  render() {
    return (
     <ImageBackground source={require('./app/img/bg_travel.jpeg')} style=\{{width: '100%', height: '100%'}}>
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
         <Text>Hi, Welcome to Creators App!</Text>
        <Button
            title="About Me"
            onPress={() => this.props.navigation.navigate('AboutMe')}
            />
      </View>
       </ImageBackground>
    );
  }
}

class DetailsScreen extends React.Component {
static navigationOptions = {
        title: 'About Me',
      };
  render() {
    return (
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
        <Text>About Me</Text>
        <Button title="Back to Home" onPress={() => this.props.navigation.navigate('Home')} />
      </View>
    );
  }
}
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-3.jpg)

Few lines of code added without modifying any other code, just add them in your code and check out the output,
It will display the title at the top nav bar.


## 5. Adding Styles to the HomeScreen and added one more Text named Sagar Kalyan.

```
 <ImageBackground source={require('./app/img/bg_travel.jpeg')} style={{width: '100%', height: '100%'}}>
      <Text style={styles.googleFont} >Sagar Kalyan</Text>
      <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
         <Text style={styles.textHome}>Hi, Welcome to Creators App!</Text>
        <Button
            title="About Me"
            onPress={() => this.props.navigation.navigate('AboutMe')}
            />
      </View>
       </ImageBackground>
 ...      
 ...
 
 export default createAppContainer(AppNavigator);

const styles = StyleSheet.create({

     googleFont: {
      fontFamily: "KaushanScript",
      flex: 1,
      alignItems: 'center',
      justifyContent: 'flex-start',
      paddingTop: 10,
      textAlign: 'center',
      fontSize: 40,
      color: '#ffffff',
      textShadowColor: 'rgba(0, 0, 0, 0.75)',
      textShadowOffset: {width: -1, height: 1},
      textShadowRadius: 5
     },

     textHome: {
      fontSize: 20,
      color: '#ffffff',
      textShadowColor: 'rgba(0, 0, 0, 0.75)',
      textShadowOffset: {width: -1, height: 1},
      textShadowRadius: 5,
      backgroundColor: '#04676D',
      padding: 5,
      margin: 5

     }

 });
       
```
![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-3.jpg)

## 6. Adding Google Font in React native (Home Screen)
We just added one more text at the top named Sagar Kalyan. And given some Styles to it.

 **fontFamily: "KaushanScript",**
 I have added this code earlier, Its not working. 
 Now, To make this line of code work, we have to download font from google font.
 
**React Native Adding Google Font - Kaushan Script**

After Selecting the font, There is download icon at the top right side. Just click on it to download.

Rename it to **KaushanScript** it's a ttf format file.
I have added downloaded file inside the app folder **(app/assets/fonts/KaushanScript.ttf)** in it,

Now add the following lines of code (At end it looks like this..)
**In package.json**
```
"jest": {
    "preset": "react-native"
  },
  "rnpm": {
    "assets": [
      "./app/assets/fonts/"
    ]
  }
}
```

Then we tell react native to link those font files for us:
Run, Using Command line:
```
react-native link
```

On Android Studio,
if you look in the file path **"android/app/src/main/assets/fonts/"**
you should see your fonts have been copied over:
**KaushanScript.ttf**


Now, We are done with the Google Fonts, Just type react native command to run the application.
```
react-native run-android
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-4.jpg)

[Reference: Adding React Native Custom Fonts](https://medium.com/react-native-training/react-native-custom-fonts-ccc9aacf9e5e)
 If you didn't understood then, just follow the instructions Step by Step.


## 7. About Me Page: We are going to add Scrollview, Image, Linking.
We will be using ResponsiveImage component instead of Image Component,
to make it better work on different devices.

Installation Process **ResponsiveImage**
Type the command in Command line - 
```
npm install react-native-responsive-image --save
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-5.jpg)
[Reference: Adding React Native Responsive Image](https://www.npmjs.com/package/react-native-responsive-image)

```
import {Platform, StyleSheet, Text, View, Button, ImageBackground, ScrollView, Image, Linking } from 'react-native';
import { createStackNavigator, createAppContainer } from "react-navigation";
import ResponsiveImage from 'react-native-responsive-image';

...
class DetailsScreen extends React.Component {
    static navigationOptions = {
            title: 'About Me',
          };
      render() {
        return (
           <ScrollView contentContainerStyle={styles.view}>
                      <View style={{ flexGrow: 1, justifyContent: 'center', alignItems: 'center', flexDirection: 'row' }}>
                            <ResponsiveImage source={require('./app/img/Sagar_kalyan.jpg')} initWidth="400" initHeight="190"/>
                      </View>
                       <Text style={styles.h1}>About Me</Text>
                       <Text style={[styles.text, styles.p]}>
                        Hi, It's Me Sagar kalyan,
                        I am struggler or hustler among millions of students in india,
                        who is very passionate about sharing his creativity and knowledge to the world.
                        Real life experiences counts the most, Although i failed in many decision making
                        for my career but now it's all helping me in some or the other perspective of lives.
                        Being true to myself had great impact in my life. So, i believe you also can do the same thing,
                        whatever i am doing right now to achieve my goals,
                        Just Implementing in your areas of interest and knowledge you have gained. Its Not enough but i have to stop...
                        </Text>
                       <Text style={[styles.text, styles.p,]} onPress={() =>
                           Linking.openURL('https://www.youtube.com/channel/UCKjZjkbjRxiks2MbTdTSh2Q/')}
                           style={styles.linkstyle}
                         >Subscribe to My Youtube Channel</Text>
                  <Text style={[styles.text, styles.p]} onPress={() =>
                           Linking.openURL('https://www.facebook.com/sagarkalyan81/')}
                           style={styles.linkstyle}
                         >Follow Me on Facebook</Text>
                   <Text style={[styles.text, styles.p]} onPress={() =>
                                     Linking.openURL('https://www.instagram.com/sagarkalyan1/')}
                                     style={styles.linkstyle}
                                   >Follow Me on Instagram</Text>
          <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
            <Text>About Me</Text>
            <Button title="Back to Home" onPress={() => this.props.navigation.navigate('Home')} />
          </View>
           </ScrollView>
        );
      }
    }
    
    ...
    
      const styles = StyleSheet.create({
    ...
    
     view: {
         marginTop: 0,
         padding: 2
       },
        h1: {
           fontSize: 22,
           alignSelf: 'center',
           marginBottom: 20
         },
         text: {
             fontSize: 16,
             lineHeight: 24,
             marginBottom: 10,
             margin: 10
           },
           p: {
             textAlign: 'left',
             marginBottom: 20
           },
           linkstyle: {
             fontStyle: 'italic',
             color: '#2962FF',
             fontSize: 25,
             lineHeight: 24,
             padding: 10
           }
       });

```

**Using:**

ResponsiveImage is expecting initWidth and initHeight props.


Adding the style properties also at the end. (view, h1, text, p, linkstyle)

**Now Run the application, to match the output display on the device.** 


```
react-native run-android
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-5.jpg)

## 8. Adding Webview (for embedding youtube videos):


**Installing:** Here's how to get started quickly with the React Native WebView.
Add react-native-webview to your dependencies
Using Command line-

```
npm install react-native-webview
```

React Native modules that include native Objective-C, Swift, Java, or Kotlin code have to be "linked" so that the compiler knows to include them in the app.

**Link native dependencies** Using Command line-

```
react-native link react-native-webview
```


**Add the Following Code in App.js:**

```
 import { WebView } from 'react-native-webview';
 
 ...
  class DetailsScreen extends React.Component {
    static navigationOptions = {
            title: 'About Me',
          };
      render() {
        return (
           <ScrollView contentContainerStyle={styles.view}>
  ...        
  <View style={{ height: 300 }}>
  <WebView
          style={{flex:1}}
          javaScriptEnabled={true}
          source={{uri: 'https://www.youtube.com/embed/FgyDAcxmUgU?rel=0&autoplay=0&showinfo=0&controls=0'}}
          />
  </View>
  ...
  <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
            <Text>About Me</Text>
            <Button title="Back to Home" onPress={() => this.props.navigation.navigate('Home')} />
      </View>
    </ScrollView>
   );
   }
}
 
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-6.jpg)

[Reference: Adding React Native Webview](https://github.com/react-native-community/react-native-webview/blob/master/docs/Getting-Started.md)


[Reference: Documentation React Native Webview](https://facebook.github.io/react-native/docs/webview)



## 9. Adding Alert and TouchableOpacity for showing User interactive Review System (Alert Box) 

**Complete Code: (In App.js)**

```
         import React, {Component} from 'react';
        import {Platform, StyleSheet, Text, View, Button, ImageBackground, ScrollView, Image, Linking, Alert, TouchableOpacity } from 'react-native';
        import { createStackNavigator, createAppContainer } from "react-navigation";
        import ResponsiveImage from 'react-native-responsive-image';
        import { WebView } from 'react-native-webview';
    
        class HomeScreen extends React.Component {
        static navigationOptions = {
                title: 'Sagar Kalyan',
              };
          render() {
            return (
             <ImageBackground source={require('./app/img/bg_travel.jpeg')} style={{width: '100%', height: '100%'}}>
              <Text style={styles.googleFont} >Sagar Kalyan</Text>
              <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
                 <Text style={styles.textHome}>Hi, Welcome to Creators App!</Text>
                <Button
                    title="About Me"
                    onPress={() => this.props.navigation.navigate('AboutMe')}
                    />
              </View>
               </ImageBackground>
            );
          }
        }
    
        class DetailsScreen extends React.Component {
        static navigationOptions = {
                title: 'About Me',
              };
         button() {
                 Alert.alert(
                   'Sagar Kalyan : My First application on React Native',
                   'Did you Like my App?',
                   [
                     {text: 'Ask me later', onPress: () => console.warn('You Can Review Me Later.')},
                     {text: 'NO', onPress: () => console.warn('No Problem, I will Improve'), style: 'cancel'},
                     {text: 'YES', onPress: () => console.warn('Thanks ! You Liked it !') },
                   ]
                 );
               }
          render() {
            return (
               <ScrollView contentContainerStyle={styles.view}>
                          <View style={{ flexGrow: 1, justifyContent: 'center', alignItems: 'center', flexDirection: 'row' }}>
                                <ResponsiveImage source={require('./app/img/Sagar_kalyan.jpg')} initWidth="400" initHeight="190"/>
                          </View>
                           <Text style={styles.h1}>About Me</Text>
                           <Text style={[styles.text, styles.p]}>
                            Hi, It's Me Sagar kalyan,
                            I am struggler or hustler among millions of students in india,
                            who is very passionate about sharing his creativity and knowledge to the world.
                            Real life experiences counts the most, Although i failed in many decision making
                            for my career but now it's all helping me in some or the other perspective of lives.
                            Being true to myself had great impact in my life. So, i believe you also can do the same thing,
                            whatever i am doing right now to achieve my goals,
                            Just Implementing in your areas of interest and knowledge you have gained. Its Not enough but i have to stop...
                            </Text>
                           <Text style={[styles.text, styles.p,]} onPress={() =>
                               Linking.openURL('https://www.youtube.com/channel/UCKjZjkbjRxiks2MbTdTSh2Q/')}
                               style={styles.linkstyle}
                             >Subscribe to My Youtube Channel</Text>
                      <Text style={[styles.text, styles.p]} onPress={() =>
                               Linking.openURL('https://www.facebook.com/sagarkalyan81/')}
                               style={styles.linkstyle}
                             >Follow Me on Facebook</Text>
                       <Text style={[styles.text, styles.p]} onPress={() =>
                                         Linking.openURL('https://www.instagram.com/sagarkalyan1/')}
                                         style={styles.linkstyle}
                                       >Follow Me on Instagram</Text>
               <View style={{ height: 300 }}>
    
                   <WebView
                          style={{flex:1}}
                          javaScriptEnabled={true}
                          source={{uri: 'https://www.youtube.com/embed/FgyDAcxmUgU?rel=0&autoplay=0&showinfo=0&controls=0'}}
                          />
               </View>
               <TouchableOpacity onPress={() => this.button()}>
                  <Text style={[styles.alert]}>Review My App</Text>
               </TouchableOpacity>
              <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>
                <Text>About Me</Text>
                <Button title="Back to Home" onPress={() => this.props.navigation.navigate('Home')} />
              </View>
               </ScrollView>
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
    
        const styles = StyleSheet.create({
    
             googleFont: {
              fontFamily: "KaushanScript",
              flex: 1,
              alignItems: 'center',
              justifyContent: 'flex-start',
              paddingTop: 10,
              textAlign: 'center',
              fontSize: 40,
              color: '#ffffff',
              textShadowColor: 'rgba(0, 0, 0, 0.75)',
              textShadowOffset: {width: -1, height: 1},
              textShadowRadius: 5
             },
    
             textHome: {
              fontSize: 20,
              color: '#ffffff',
              textShadowColor: 'rgba(0, 0, 0, 0.75)',
              textShadowOffset: {width: -1, height: 1},
              textShadowRadius: 5,
              backgroundColor: '#04676D',
              padding: 5,
              margin: 5
    
             },
              view: {
                      marginTop: 0,
                      padding: 2
                    },
                     h1: {
                        fontSize: 22,
                        alignSelf: 'center',
                        marginBottom: 20
                      },
                      text: {
                          fontSize: 16,
                          lineHeight: 24,
                          marginBottom: 10,
                          margin: 10
                        },
                        p: {
                          textAlign: 'left',
                          marginBottom: 20
                        },
                        linkstyle: {
                          fontStyle: 'italic',
                          color: '#2962FF',
                          fontSize: 25,
                          lineHeight: 24,
                          padding: 10
                        },
                         alert:{
                                     backgroundColor: '#FF0000',
                                     color: '#FFF',
                                     textShadowColor: 'rgba(0, 0, 0, 0.50)',
                                     textShadowOffset: {width: -1, height: 1},
                                     textShadowRadius: 2,
                                     padding: 10,
                                     margin: 20,
                                     textAlign: 'center'
                                   }
    
         });
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-6.jpg)

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-7.jpg)

### This is the final modified code with the change of Backgorund Image and Using Opacity to make it cool and great App:

```

    import React, {Component} from 'react';
    import {Platform, StyleSheet, Text, View, Button, ScrollView, ImageBackground, Image, Linking, Alert, TouchableOpacity } from 'react-native';
    import { createStackNavigator, createAppContainer } from "react-navigation";
    import ResponsiveImage from 'react-native-responsive-image';
    import { WebView } from 'react-native-webview';

    class HomeScreen extends React.Component {
    static navigationOptions = {
        title: 'Sagar Kalyan',
      };
      render() {
        return (
        <ImageBackground source={require('./app/img/bg_travel.jpg')} style={{width: '100%', height: '100%'}}>
                <Text style={styles.googleFont} >Sagar Kalyan</Text>

                   <View style={{ flex: 1, alignItems: "center", justifyContent: "center" }}>

                          <Text style={styles.textHome}>Hi, Welcome to Creators App!</Text>

                           <Button
                                    title="About Me"
                                    onPress={() => this.props.navigation.navigate('AboutMe')}
                                  />
                        </View>
            </ImageBackground>
        );
      }
    }

    class DetailsScreen extends React.Component {
    static navigationOptions = {
        title: 'About Me',
      };
    button() {
        Alert.alert(
          'Sagar Kalyan : My First application on React Native',
          'Did you Like my App?',
          [
            {text: 'Ask me later', onPress: () => console.warn('You Can Review Me Later.')},
            {text: 'NO', onPress: () => console.warn('No Problem, I will Improve'), style: 'cancel'},
            {text: 'YES', onPress: () => console.warn('Thanks ! You Liked it !') },
          ]
        );
      }
      render() {
        return (
            <ScrollView contentContainerStyle={styles.view}>
            <View style={{ flexGrow: 1, justifyContent: 'center', alignItems: 'center', flexDirection: 'row' }}>
                  <ResponsiveImage source={require('./app/img/Sagar_kalyan.jpg')} initWidth="400" initHeight="190"/>
            </View>
             <Text style={styles.h1}>About Me</Text>
             <Text style={[styles.text, styles.p]}>
              Hi, It's Me Sagar kalyan,
              I am struggler or hustler among millions of students in india,
              who is very passionate about sharing his creativity and knowledge to the world.
              Real life experiences counts the most, Although i failed in many decision making
              for my career but now it's all helping me in some or the other perspective of lives.
              Being true to myself had great impact in my life. So, i believe you also can do the same thing,
              whatever i am doing right now to achieve my goals,
              Just Implementing in your areas of interest and knowledge you have gained. Its Not enough but i have to stop...
              </Text>
              <Text style={[styles.text, styles.p,]} onPress={() =>
                       Linking.openURL('https://www.youtube.com/channel/UCKjZjkbjRxiks2MbTdTSh2Q/')}
                       style={styles.linkstyle}
                     >Subscribe to My Youtube Channel</Text>
              <Text style={[styles.text, styles.p]} onPress={() =>
                       Linking.openURL('https://www.facebook.com/sagarkalyan81/')}
                       style={styles.linkstyle}
                     >Follow Me on Facebook</Text>
               <Text style={[styles.text, styles.p]} onPress={() =>
                                 Linking.openURL('https://www.instagram.com/sagarkalyan1/')}
                                 style={styles.linkstyle}
                               >Follow Me on Instagram</Text>

                  <View style={{ height: 300 }}>

                          <WebView
                                  style={{flex:1}}
                                  javaScriptEnabled={true}
                                  source={{uri: 'https://www.youtube.com/embed/FgyDAcxmUgU?rel=0&autoplay=0&showinfo=0&controls=0'}}
                          />
                         </View>

                   <TouchableOpacity onPress={() => this.button()}>
                            <Text style={[styles.alert]}>Review My App</Text>
                          </TouchableOpacity>

                  <View style={{ flex: 1, alignItems: "center", justifyContent: "flex-start" }}>
                   <Text >Homepage</Text>
                   <Button title="Back to Home" onPress={() => this.props.navigation.navigate('Home')} />
                   </View>
                </ScrollView>

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


    const styles = StyleSheet.create({

     googleFont: {
      fontFamily: "KaushanScript",
      flex: 1,
      alignItems: 'center',
      justifyContent: 'flex-start',
      paddingTop: 10,
      textAlign: 'center',
      fontSize: 40,
      color: '#ffffff',
      textShadowColor: 'rgba(0, 0, 0, 0.75)',
      textShadowOffset: {width: -1, height: 1},
      textShadowRadius: 5
     },

     textHome: {
      fontSize: 20,
      color: '#ffffff',
      textShadowColor: 'rgba(0, 0, 0, 0.75)',
      textShadowOffset: {width: -1, height: 1},
      textShadowRadius: 5,
      backgroundColor: 'rgba(255,255,255,0.3)',
      padding: 5,
      margin: 5

     },
      view: {
         marginTop: 0,
         padding: 2
       },
        h1: {
           fontSize: 22,
           alignSelf: 'center',
           marginBottom: 20
         },
         text: {
             fontSize: 16,
             lineHeight: 24,
             marginBottom: 10,
             margin: 10
           },
           p: {
             textAlign: 'left',
             marginBottom: 20
           },
           linkstyle: {
             fontStyle: 'italic',
             color: '#2962FF',
             fontSize: 25,
             lineHeight: 24,
             padding: 10
           },
           alert:{
             backgroundColor: '#FF0000',
             color: '#FFF',
             textShadowColor: 'rgba(0, 0, 0, 0.50)',
             textShadowOffset: {width: -1, height: 1},
             textShadowRadius: 2,
             padding: 10,
             margin: 20,
             textAlign: 'center'
           }
    });
```

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-8.jpg)


### Added Mobile Icon as logo of an Application:

![Image](https://raw.githubusercontent.com/sagarkalyan/react-native/master/images/Untitled-9.jpg)


Therefore, Running the Application Successfully. We accomplished our task for this tutorial on React Native.
Hopefully, It was easy understood.

Thanks
Sagar kalyan

