<div align="center">
 <h2>TailPOS</h2>
 <p align="center">
  <p>TailPOS  an Offline First Open Source POS for ERPNext</p>
  <a href='https://play.google.com/store/apps/details?id=com.tailpos&hl=en&pcampaignid=MKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img alt='Get it on Google Play' src='https://play.google.com/intl/en_us/badges/images/generic/en_badge_web_generic.png' width='25%' /></a>
 </p>
</div>

### Showcase

![Showcase](showcase.gif)

### Features

<b> o Two Way Sync to ERPNext </b>
  Two way syncing to an ERPNext instance for a full suite of back-office functionalities.

<b> o Offline-first Approach </b>
  Continue to make sales and keep running the business even no  internet or unstable.

<b> o Mobile POS </b>
  Uses the tablet for a lightweight setup. Built-in rear camera of the tablet can be used as a barcode scanner. Any bluetooth barcode scanner is compatible with TailPOS app as well.

<b> o Print receipts </b>
  Print sales receipts for customers using any ESC/P receipt printer.

<b> o Multiple payment modes </b>
  Can process credit card,mobile payments and cash.

<b> o Discounts Program </b>
  Can apply discount to an invoice or on specific items.

<b> o Inventory Management </b>
  Keep track of stock levels easily. Easy-to-use menu for item maintenance such as creating and updating item information.

<b> o Sales Reports </b>
  Can generate X and Z readings and attendant shift sales totals.

### License
This project is released under the GPLv3 license, for more details, take a look at the LICENSE file in the source.

### How To Install

First, you'll need NodeJS and NPM:

```terminal
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
nodejs -v
v8.4.0
```

Install development tools to build native addons:
```terminal
sudo apt-get install gcc g++ make
```
Install the Yarn package manager, run:
```terminal
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn
```

Then you can install react-native using `npm`

```terminal
sudo npm install -g react-native-cli
```

Now you need to install Java/ Android

```terminal
sudo apt-get install default-jre
sudo apt-get install default-jdk

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

* Install Android
* Install Android SDK requirements

```terminal
cd ~
mkdir android-sdk
cd android-sdk
wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
sudo apt-get install unzip
unzip sdk-tools-linux-3859397.zip
```

We add the path of our Android SDK tools to .bashrc so that we have access to the Android tools.
```
cd ~
nano .bashrc

# Add these lines to the top of the file
export ANDROID_HOME=$HOME/android-sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools

# CTRL+O (uppcase o) to save
# CTRL+X to exit

source ~/.bashrc
```

Now we have access to the android command
```terminal

android update sdk --no-ui
# Answer 'y' to all prompts

sdkmanager "platforms;android-23" "build-tools;23.0.1" "add-ons;addon-google_apis-google-23"
```

Installing tailpos mobile app
```terminal
cd ~
mkdir Projects
cd Projects
git clone https://gitlab.com/bailabs/tailpos-mobile.git
cd tailpos-mobile
yarn
```

Updating react-native-camera modules
  * remove buildscript section

```terminal
  buildscript {
  repositories {
    jcenter()
    maven {
      url 'https://maven.google.com'
    }
  }

  dependencies {
    classpath 'com.android.tools.build:gradle:3.0.0'
  }
}
```

  * compileOnly to provided
  * implemenation to compile

```terminal
cd ~
nano Projects/tailpos-mobile/node_modules/react-native-camera/android/build.gradle
```

Updating react-native-maps modules
  * compileOnly to provided
  * implemenation to compile

```terminal
cd ~
nano Projects/tailpos-mobile/node_modules/react-native-maps/lib/android/build.gradle
```


Updating react-native-bluetooth-serial modules
  * remove @Override in line 23 (the second @Override)

```terminal
cd ~
nano Projects/tailpos-mobile/node_modules/react-native-bluetooth-serial/android/src/main/java/com/rusel/RCTBluetoothSerial/RCTBluetoothSerialPackage.java
```


Building tailpos

```terminal
cd ~
cd Projects/tailpos-mobile
react-native run-android
```





