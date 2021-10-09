# CreatePrivatePod

1. create new repo for your pod 
2. inside your git repo create a new foler and name it with your pod name
    1. inside this folder with be your pod classes and files organize this folder as you wish 
    2. but a recommended patter is to create a folder named "Classes" and inside this folder create a new swift file and name it ReplaceMe.swift for now
3. open terminal and cd to the root of your git repo not root of your project , meaning next to "readme" & "license" files
4. use this command to create pod spec file : <br/>
 pod spec create [POD_NAME] 
5. update these values <br/>
    - spec.summary "should be a simple words about the pod"
    - spec.description "should be a long description about the pod"
    - spec.homepage "pod git url or your home website url"
    - spec.license "should be like this : "{ :type => "MIT", :file => "FILE_NAME" }"
    - spec.platform should be like " spec.platform     = :ios, "5.0" " with min ios version supported for your pod 
    - spec.source "git url with your repo git url"
    - spec.source_files "with your folders path to your code"
6. create new ios app project next to the pod project and name it example
7. so now your git repo is like this : <br/>
    - [YOUR_POD_NAME_FOLDER]
    - example folder
    - [YOUR_POD_NAME].podspec
    - LICENSE
    - README
8. open terminal and cd to example project 
9. run pod init command 
10. edit pod file by add <br/>
    pod '[YOUR_POD_NAME]', :path => '../'
11. run pod install command
12. open example.xcworkspace 
13. expand pods section in the right panel in xcode 
14. expand "Development Pods" folder 
15. you will find the previously created ReplaceMe.swift file , but in the root not in classes folder 
16. if you reveal the ReplaceMe.swift file in finder you will find the classes folder , and here is the place where you should put all your pod files 
17. note the your extenstions and classes needs to be public to be accessabile from out side the pod 
18. remove ReplaceMe.swift file 
19. you can use your pod like : pod '[POD_NAME]', :git => '[POD_URL]', :branch => '[BRANCH_NAME]', :tag => '[TAG]'
20. inside your [POD_NAME].podspec file you will find a line like this line <br/>
    { :git => "[YOUR_POD_GIT_LINK]", :tag => "#{spec.version}" }<br/>
    - while you creating you pod using git you can create a tag on each commit or one commit after a series of commits until you finish the new version of your pod 
    - for example you created 10 commits until you finished the new version of your pod , you can tag the last commit with the new version number 
    - so the user to be able to use this tag as a version inside the podfile to only install commits until this version , so if you crrated a new version and the user don't need it he can only install the previouse version 
    - VIP_NOTE: you can't specify the version while you are using ':git' attribute in the pod file but you can use ':tag => '[TAG]'' attribute instead to be like this <br/>
    pod '[POD_NAME]', :git => '[POD_URL]', :branch => '[BRANCH_NAME]', :tag => '[TAG]'


# Sub Pods
1. you can create a sub pods and use it like this 'pod '[POD_NAME]/[SUB_POD_NAME]'
2. inside your [POD_NAME].podspec file add these lines to create a sub pod 
    ```
    spec.subspec '[YOUR_SUB_POD_NAME]' do |[VARIABLE_TO_REFERENCE_THE_POD]]|
        [VARIABLE_TO_REFERENCE_THE_POD].source_files = '[POD_FILES_PATH]'
    end
    ```
# Pod Depndency
spec.dependency 'Alamofire'
<!-- 
# Sub Pods Section
  spec.subspec 'AccessabilityId' do |accessabilityId|
    accessabilityId.source_files   = 'AccessabilityId/AccessabilityId/**/*'
    accessabilityId.dependency 'Extenstions/UIView'
  end -->