# Clearing Quarantine for Casks

Every now and then I install an app using `brew cask` and Mojave/Catalina spends ages "verifying" it upon launch.

The solution for that is to clear the `com.apple.quarantine` from it (and any internal bundles, recursively), using:

```bash
sudo xattr -dr com.apple.quarantine /Applications/AppName.app
```

Obviously, you should only do this for apps you trust.

