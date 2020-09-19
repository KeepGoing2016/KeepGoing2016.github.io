---
title: Cocoapods小结
date: 2020-09-18 18:01:26
tags:
---

这是我第一篇博客，不知道从哪里开始，一脸茫然。只能以小结的形式梳理自己日常工作所积累的点点滴滴。
##### Cocoapods安装：
* 更换源
   
```
gem sources --remove https://rubygems.org/
gem sources --add https://gems.ruby-china.com/
```
* 安装

```
sudo gem install -n /usr/local/bin cocoapods
pod setup  从镜像源中下载podspec索引文件到～/cocoapods/repo
```
##### Podfile语法
[官方语法](https://guides.cocoapods.org/syntax/podfile.html#platform)
```
source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '6.0'
inhibit_all_warnings! //忽略警告

xcodeproj 'MyProject'

pod 'ObjectiveSugar', '~> 0.5'

target 'MyProject' do
  pod 'OCMock', '~> 2.0.1'
  pod 'PonyDebugger', :configurations => ['Debug', 'Beta']
  pod 'PonyDebugger', :configuration => 'Debug'
  pod 'SSZipArchive', :modular_headers => true
  pod 'PonyDebugger', :source => 'https://github.com/CocoaPods/Specs.git'
  pod 'QueryKit', :subspecs => ['Attribute', 'QuerySet']
  pod 'QueryKit/Attribute'
  pod 'AFNetworking', :path => '~/Documents/AFNetworking'
  pod 'AFNetworking', :git => 'https://github.com/gowalla/AFNetworking.git', :branch => 'dev'
  pod 'AFNetworking', :git => 'https://github.com/gowalla/AFNetworking.git', :tag => '0.7.0'
  pod 'AFNetworking', :git => 'https://github.com/gowalla/AFNetworking.git', :commit => '082f8319af'
  pod 'JSONKit', :podspec => 'https://example.com/JSONKit.podspec'
  pod 'SSZipArchive', :inhibit_warnings => true

end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    puts #{target.name}
  end
end
```
##### Cocoapods进阶
* 安装不同版本的cocoapods
 
```
sudo gem install cocoapods -v 0.39.0 -n /usr/local/bin 安装指定版本的cocoapods
```

* 不同cocoapods版本之间的切换

[Bundler](https://bundler.io) 是一个 Ruby 项目的管理工具,可以用来管理cocoapods不同版本的切换。

```
gem install bundler
bundle init  该方法执行后会生成Gemfile和Gemfile.lock文件
bundle install
bundle exec pod install
```

Gemfile文件语法：

```
source "https://rubygems.org"
gem 'cocoapods','1.4.0'
```

* 多版本ruby管理
  
```
curl -L get.rvm.io | bash -s stable && source ~/.rvm/scripts/rvm
rvm list known
rvm install 2.6.3
rvm use <Version>
rvm use <Version> --default，可设置默认 ruby 版本
```

* 一些常用命令

```
sudo gem uninstall cocoapods -v 0.39.0
pod cache clean --all或者指定某个库
pod cache list
```
  



