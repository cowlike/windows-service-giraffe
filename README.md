# Overview

This is a modified version of the basic template-generated Giraffe web app using .NET Core 3.1 and F#. The code was first creating using the [Getting Started guide](https://github.com/giraffe-fsharp/Giraffe#getting-started) on the Giraffe site. After creating the app using the template, I modified it to run as a Windows service and then published it for Windows 7 (see below) as a test to make sure it would run there.

## publish it as a single executable

This is being published using the `win7-x86` RID in order to publish on a 32-bit Windows 7 machine. (not recommended)

```bash
dotnet publish -r win7-x86 \
    -c Release -o /c/apps/testapps/giraffetest \
    -p:PublishSingleFile=True \
    -p:PublishTrimmed=True \
    -p:UseAppHost=True
```

## service creation, starting, stopping, etc

Use the `sc` command:

```bash
sc create “Sample Service” binPath=/c/apps/testapps/workertest/Main.exe
sc query "Sample Service"
sc start "Sample Service"
sc stop "Sample Service"
sc delete "Sample Service"
```
