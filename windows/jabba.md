# Jabba - Java Version Manager on Windows, only available on PowerShell

## list remote available jdks
```sh
jabba ls-remote
```

## install jdk
```sh
jabba install openjdk@1.17.0
```

## list all installed JDK's
```sh
jabba ls
```

## switch to a different version of JDK (it must be already `install`ed)
```sh
jabba use adopt@1.8
jabba use openjdk@1.17.0
```

## setup project needed jdk apply shortcut 
```sh
cd <project_dir>
echo "<installed_sdk_in_jabba ls>" > .jabbarc
jabba use 
```