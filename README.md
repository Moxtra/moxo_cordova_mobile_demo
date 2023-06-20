![moxo](https://assets-global.website-files.com/612ecbcc615e87b0b9b38524/62037243f5ede375a8705a34_Moxo-Website-Button.svg)

[ [Introduce](#introduce) &bull; [How to run](#how-to-run)]

## Introduce

A cordova demo app based on [cordova-plugin-moxo](https://github.com/Moxtra/cordova-plugin-moxo)

### Requirement

* iOS 13.0+
* Android 4.4+

## How to run

1. Clone this repo or download zip file, go to root directory of the project.
   Run below command to get dependencies:

```
npm install
```

2. Add cordova platforms and install plugins:

```
cd src-cordova
cordova platform add ios
//or cordova platform add android
cordova plugin add @moxtradeveloper/cordova-plugin-moxo
```
2. Add Moxo environment details to .env file in root directory of the project. For example:
```
VUE_APP_DOMAIN=YOUR_DOMAIN
VUE_APP_CLIENT_ID=YOUR_CLIENT_ID
VUE_APP_CLIENT_SECRET=YOUR_CLIENT_SECRET
VUE_APP_ORG_ID=YOUR_ORG_ID
VUE_APP_EMAIL=YOUR_EMAIL
#VUE_APP_UNIQUE_ID=
```
DOMAIN, CLIENT_ID, CLIENT_SECRET, ORG_ID are required. Choose one of UNIQUE_ID and EMAIL as user identity.
By default, this project is using EMAIL. If you prefer UNIQUE_ID, please assign a value and uncomment UNIQUE_ID.


3. When dependencies are ready, run below command to run app:
Note: this command should run in root directory
```
npm run cordova-build-ios
or 
npm run cordova-build-android
```
