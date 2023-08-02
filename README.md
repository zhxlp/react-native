# README


## Initialize environment

- Install Docker

- Creating Gradle Home Storage

```
docker volume create gradle_home
```

- git clone code

- Install NPM dependencies

```
cd react-native
git checkout 0.66-stable
yarn
```

- modify version

```
./scripts/bump-oss-version.js -v 0.66.6
```

## build 

- build android aar

```
docker run --rm --name rn-build -v $PWD:/pwd -v gradle_home:/root/.gradle -w /pwd reactnativecommunity/react-native-android:6.2 /bin/sh -c "./gradlew --info installArchives"
```

- npm pack

```
npm pack
```

- upload react-native-0.66.6.tgz


## use

- modify project `package.json`

```
...
"dependencies": {
...
"react-native": "https://test.com/react-native/react-native-0.66.6.tgz",
...
```

 - Reinstall NPM dependencies

 ```
 rm -rf node_modules
 yarn --force
 cd ios
 pod install
 ```
