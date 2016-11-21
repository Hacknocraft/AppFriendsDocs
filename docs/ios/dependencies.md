## Dependencies List
AppFriends SDKs have several external dependencies with open source libraries. We are committed to always update our SDK to be compatible the latest version of the dependencies

Dependencies   |   License Type   |   AppFriendsCore  |  AppFriendsUI   |  Version (swift2.3) |  Version (swift3)                    
-------------  | ---------------  | ----------------  | --------------- | ------------------  | -------------------
Alamofire                 | MIT   | ✔                 | ✔               | ~> 3.5.1            | ~> 4.0.1        
JWT                       | MIT   | ✔                 | ✔               | ~> 2.1.0            | ~> 2.1.0                     
CoreStore                 | MIT   | ✔                 | ✔               | ~> 2.1.3            | ~> 2.1.3     
Cloudinary                | MIT   | ✔                 | ✔               | ~> 1.0.15           | ~> 1.0.15    
Socket.IO-Client-Swift    | MIT   | ✔                 | ✔               | ~> 7.0.3            | ~> 8.1.1      
SlackTextViewController   | MIT   | ✘                 | ✔               | ~> 1.9.5            | ~> 1.9.5         
CLTokenInputView          | MIT   | ✘                 | ✔               | ~> 2.3.0            | ~> 2.3.0     
SESlideTableViewCell      | MIT   | ✘                 | ✔               | ~> 0.7.1            | ~> 0.7.1     
AFDateHelper              | MIT   | ✘                 | ✔               | ~> 3.5.3            | ~> 1.9.5     
AlamofireImage            | MIT   | ✘                 | ✔               | ~> 2.5              | ~> 3.1.0     


## Podfile
To support Swift2.3, extra specifiers are needed. Below illustrates how the Podfile looks in Swift2.3 and Swift3.

### Swift 3
```
pod 'AppFriendsUI'
```

### Swift 2.3
```
pod 'AppFriendsUI', :git => 'https://github.com/laeroah/AppFriendsUI.git', :branch => 'swift2.3'
pod 'AppFriendsCore', :git => 'https://github.com/laeroah/AppFriendsCoreFramework.git', :branch => 'swift2.3'
pod 'AFDateHelper', :git => 'https://github.com/laeroah/DateExtension.git'
pod 'FontAwesome.swift', :git => 'https://github.com/thii/FontAwesome.swift.git', :branch => 'swift-2.3'
pod 'Socket.IO-Client-Swift', :git => 'https://github.com/socketio/socket.io-client-swift.git', :branch => 'swift2.3'

post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |configuration|
            configuration.build_settings['SWIFT_VERSION'] = "2.3"
        end
    end
end

```
