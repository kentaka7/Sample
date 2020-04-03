# CDNの利用
# source 'https://cdn.cocoapods.org/'

# Uncomment the next line to define a global platform for your project
platform :ios, '11.0'

use_frameworks!

def commonInstall
  pod 'SwiftLint'
  pod 'LicensePlist'
  pod 'SwiftGen'
  pod 'Fabric'
  pod 'Crashlytics'
end

def firebase
  pod 'Firebase/Analytics'
  pod 'Firebase/Messaging'
  pod 'Firebase/RemoteConfig'
  pod 'Firebase/Performance'
end

# Pods for Vitamin
target 'Sample' do
  commonInstall
  firebase
  
  # Pods for testing
  target 'SampleTests' do
    inherit! :search_paths
    firebase
  end
  
end

post_install do |installer|
    puts 'Removing static analyzer support'
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['OTHER_CFLAGS'] = "$(inherited) -Qunused-arguments -Xanalyzer -analyzer-disable-all-checks"
        end
    end
end


