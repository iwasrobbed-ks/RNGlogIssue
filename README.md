# Reproduction Steps

Reference issue: https://github.com/facebook/react-native/issues/20772

1. Install CocoaPods (`gem install cocoapods`)
2. Clone this repo and `cd` into the directory
3. Run `pod install`
4. Notice the error below during the `glog` install step:

```
Installing glog (0.3.4)
...
/bin/bash: line 27: ./configure: No such file or directory
```

