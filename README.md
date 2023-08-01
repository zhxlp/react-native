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

## build 

- build android aar

```
docker run --rm --name rn-build -v $PWD:/pwd -v gradle_home:/root/.gradle -w /pwd reactnativecommunity/react-native-android:6.2 /bin/sh -c "./gradlew --info installArchives"
```

- npm pack

```
npm pack
mv react-native-0.66.5.tgz "react-native-0.66.5-$(date '+%Y%m%d%H%M').tgz"
```

## use

- modify project `package.json`

```
...
"dependencies": {
...
"react-native": "https://test.com/react-native/react-native-0.66.5-202308011817.tgz",
...
```

 - Reinstall NPM dependencies

 ```
 yarn --force
 ```