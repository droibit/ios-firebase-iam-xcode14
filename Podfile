# Uncomment the next line to define a global platform for your project
platform :ios, '14.0'

target 'Firebase-IAM' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks! :linkage => :static

  # Pods for Firebase-IAM
  pod 'Firebase', '9.6.0'
  pod 'Firebase/Analytics', '9.6.0'
  pod 'Firebase/InAppMessaging', '9.6.0'
end


post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      if config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'].to_f < 14.0
        config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '14.0'
      end      
    end

    # ref. https://github.com/CocoaPods/CocoaPods/issues/8891#issuecomment-1201465446
    if target.respond_to?(:product_type) and target.product_type == "com.apple.product-type.bundle"
      target.build_configurations.each do |config|
          config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      end
    end
  end
end
