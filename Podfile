source "https://cdn.cocoapods.org"

workspace "./Moments.xcworkspace"
project "./Moments/Moments.xcodeproj"

platform :ios, "14.0"
use_frameworks!

inhibit_all_warnings!

def dev_pods
  pod "SwiftLint", "=0.42.0", configurations: ["Debug"]
  pod "SwiftGen", "=6.4.0", configurations: ["Debug"]
end

def core_pods
  pod "RxSwift", "=5.1.1"
  pod "RxRelay", "=5.1.1"
  pod "Alamofire", "=5.3.0"
end

target "Moments" do
  dev_pods
  core_pods
end

target "MomentsTests" do
  core_pods
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings.delete "IPHONEOS_DEPLOYMENT_TARGET"
      config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
    end
  end
end
