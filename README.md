# Thumbnail handler demonstration

This project is designed to create *Windows Shell Extensions* which used to create thumbnail. Currently, MSDN recommended developers to derive Thumbnail Provider class from **IInitializeWithStream** instead of **IInitializeWithFile** because of system security. But in some conditions, we would like to deal files with its full path. Obviously, **IInitializeWithStream** is not what we want in this case. It's HARD to work with IInitializeWithFile since there is little information about how to use **IInitializeWithFile** on the Internet. **WE ARE ON OUR OWN**.
  
Actually, only three steps are needed to make the initialization with **IInitializeWithFile** working:
1. Derive your Thumbnail Provider class from IInitializeWithFile instead of IInitializeWithStream. Change the overridden Initialize function signature accordingly.
2. Make sure all reference to IInitializeWithStream is replaced with IInitializeWithFile taking special care of the one from the QueryInterface method implementation.
3. Make sure the registry key DisableProcessIsolation value is set to one otherwise initialization with file name will never get called. 

## How to use

- clone repo using following command:
```bash
git clone https://github.com/csuft/WindowsThumbnail.git
```
- generate Visual Studio Solution to build.
- register the COM component with:

```bash
regsvr32 WindowsThumbnail.dll      // for registration
regsvr32 /u WindowsThumbnail.dll   // for unregistration
```

## Interfaces

* IInitializeWithStream
* IInitializeWithFile
* IInitializeWithItem

## References

1. http://www.cnblogs.com/csuftzzk
2. http://slion.net/view/Dev/MakingOfMs3dThumbnailProvider
3. http://stackoverflow.com/questions/24232451/debugging-shell-extensions-in-win-7-and-8-1
4. https://code.msdn.microsoft.com/windowsapps/CppShellExtThumbnailHandler-32399b35