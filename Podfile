NODE_MODULES_PATH = Pathname('./node_modules').freeze
unless NODE_MODULES_PATH.exist?
  raise "No node_modules found at #{NODE_MODULES_PATH.parent}. " \
    'You should run `make install` before running `pod install`'
end

# Helpers for ReactNative
def react_pod(name, options)
  if options[:npm_path]
    options[:path] = (NODE_MODULES_PATH + options[:npm_path]).to_s
    options.delete(:npm_path)
  end
  puts "React pod path: #{options[:path]}"
  pod name, options
end

# Default platform for most targets
platform :ios, '10.0'

# Ignore all warnings from all pods
inhibit_all_warnings!

# Use frameworks for Swift
use_frameworks!

def react_pods
  react_pod 'React', npm_path: 'react-native', subspecs: %w[
    Core
    CxxBridge
    RCTImage
    RCTNetwork
    RCTText
    RCTLinkingIOS
    RCTWebSocket
    RCTAnimation
  ]
  # Required by ReactNative
  react_pod 'yoga', npm_path: 'react-native/ReactCommon/yoga'
  react_pod 'DoubleConversion', npm_path: 'react-native/third-party-podspecs'
  react_pod 'glog', npm_path: 'react-native/third-party-podspecs'
  react_pod 'Folly', npm_path: 'react-native/third-party-podspecs'
end

target 'RNGlogIssue' do
  project 'RNGlogIssue.xcodeproj'
  react_pods
end