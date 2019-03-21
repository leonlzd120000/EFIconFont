# EFIconFont

[![CI Status](https://img.shields.io/travis/EFPrefix/EFIconFont.svg?style=flat)](https://travis-ci.org/EFPrefix/EFIconFont)
[![Version](https://img.shields.io/cocoapods/v/EFIconFont.svg?style=flat)](https://cocoapods.org/pods/EFIconFont)
[![License](https://img.shields.io/cocoapods/l/EFIconFont.svg?style=flat)](https://cocoapods.org/pods/EFIconFont)
[![Platform](https://img.shields.io/cocoapods/p/EFIconFont.svg?style=flat)](https://cocoapods.org/pods/EFIconFont)
[![QQ Group](https://img.shields.io/badge/QQ群-769966374-32befc.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAQCAMAAAARSr4IAAAA4VBMVEUAAAAAAAAAAAD3rwgAAAAAAADpICBuTQNUDAwAAAAAAAAAAAAAAADnICAAAAAAAACbFRUAAAD5rgkfFgEAAADHGxu1GBhGOyQ6LhMPCgAAAAB0UQRbDAziHh7hHh5HRUEAAAAPAgIQCwEQEBAdBAQgICAvIQIvLy8+LAJAQEBJCgpWRBpbW1tfX19gYGBqZVptTARvb299VwSAgICEhISHh4ePhnGbbAWgoKCseAawsLC7gwbAwMDExMTFrKzLjgfoHx/powfqpAjvZGTw8PDxcnLxenrzj4/5rgj5x8f///9y6ONcAAAAIHRSTlMAECAgMEBQVlhggZGhobHBwdHR3eHh4+fp7/Hx9/f5+3tefS0AAACkSURBVHjaNc1FAsJAEAXRDj64BAv2IbgEd2s0gfsfiJkAtXurIpkWMQBd0K8O3KZfhWEeW9YB8LnUYY2Gi6WJqJIHwKo7GAMpRT/aV0d2BhRD/Xp7tt9OGs2yYoy5mpUxc0BOc/yvkiQSwJPZtu3XCdAoDtjMb5k8C9KN1utx+zFChsD97bYzRII0Ss2/7IUliILFjZKV8ZLM61xK+V6tsHbSRB+BYB6Vhuib7wAAAABJRU5ErkJggg==)](http://shang.qq.com/wpa/qunwpa?idkey=d0f732585dcb0c6f2eb26bc9e0327f6305d18260eeba89ed26a201b520c572c0)

一个普通的 icon font 封装，帮助你更便捷地在你的工程中使用 icon font。

> [English Introduction](https://github.com/EFPrefix/EFIconFont/blob/master/README.md)

## 预览

| 1 | 2 | 3 |
|:-:|:-:|:-:|
| ![](https://github.com/EFPrefix/EFIconFont/blob/master/Assets/1.png?raw=true) | ![](https://github.com/EFPrefix/EFIconFont/blob/master/Assets/2.png?raw=true) | ![](https://github.com/EFPrefix/EFIconFont/blob/master/Assets/3.png?raw=true) |

## 示例

1. 利用 `git clone` 命令下载本仓库；
2. 利用 cd 命令切换到 Example 目录下，执行 `pod install` 命令；
3. 随后打开 `EFIconFont.xcworkspace` 编译即可。

或执行以下命令：

```bash
git clone git@github.com:EFPrefix/EFIconFont.git; cd EFIconFont/Example; pod install; open EFIconFont.xcworkspace
```

## 需求

- iOS 8.0+
- Swift 4.2+

## 安装

EFIconFont 可以通过 [CocoaPods](http://cocoapods.org) 进行获取。只需要在你的 Podfile 中添加如下代码就能实现引入：

```ruby
pod 'EFIconFont'
```

可以通过 subspecs 方式引入本库已集成的 AntDesign 和 FontAwesome 资源：

```ruby
pod 'EFIconFont', :subspecs => ['Core', 'AntDesign', 'FontAwesome']
```

然后，执行如下命令即可：

```bash
pod install
```

## 使用

### 1. 核心

实现 `EFIconFontProtocol` 协议的对象，能够将自身转换为 `NSAttributedString` 或 `UIImage`，该协议内容如下：

```swift
public protocol EFIconFontProtocol {

    // `name` is not necessarily equal to .ttf file name
    var name: String { get }

    // `path` is path of .ttf file
    var path: String { get }

    // `unicode` is unique identifier of particular icon
    var unicode: String { get }
}
```

- name：字体名，与 .ttf 文件名并不一定相等，可通过 [BirdFont](https://birdfont.org) 查看其 Name 属性取得；
- path：.ttf 文件路径；
- unicode：某符号的 unicode。

实现该协议的对象，可通过调用下列方法进行转换输出为字符串和图片，可改变前景色和大小：

```swift
// MARK:- String
func attributedString(size fontSize: CGFloat, color: UIColor? = nil) -> NSAttributedString?

// MARK:- Image
func image(size fontSize: CGFloat, color: UIColor? = nil) -> UIImage?
func image(size imageSize: CGSize, color: UIColor? = nil) -> UIImage?
```

### 2. 扩展

本库已在 AntDesign 与 FontAwesome 这两个 subspec 中集成了 AntDesign 与 FontAwesome 的免费资源，需要使用的同学引入即可，使用方式如下：

```swift
EFIconFontAntDesign.addteam.attributedString(size: 24)
EFIconFontFontAwesomeBrands.adobe.attributedString(size: 32, color: UIColor.blue)
EFIconFontFontAwesomeRegular.addressBook.image(size: 24, color: UIColor.red)
EFIconFontFontAwesomeSolid.alignLeft.image(size: CGSize(width: 36, height: 48), color: UIColor.green)
```

### 3. 其它

一些 icon font 资源站点素材的爬取以及代码生成方式：

- [iconfont.cn](https://github.com/EFPrefix/EFIconFont/blob/master/Extend/iconfont.md)
- [fontawesome.com](https://github.com/EFPrefix/EFIconFont/blob/master/Extend/fontawesome.md)

## 字体包

| 名称 | 数量 | 文件大小 | 描述 | 预览 |
|:-|:-|:-|:-|:-|
| AntDesign | 557 | 127KB | AntDesign 所属图标库 | [iconfont.cn](https://www.iconfont.cn/collections/detail?cid=9402) |
| FontAwesome | 1516 | 356KB | FontAwesome 所属的免费图标库 | [fontawesome.com](https://fontawesome.com/icons?d=gallery&m=free) |

## 作者

EyreFree, eyrefree@eyrefree.org

## 协议

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/License_icon-mit-88x31-2.svg/128px-License_icon-mit-88x31-2.svg.png">

EFIconFont 基于 MIT 协议进行分发和使用，更多信息参见 [协议文件](LICENSE)。