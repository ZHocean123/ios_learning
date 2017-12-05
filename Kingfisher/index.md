Kingfisher is a lightweight, pure-Swift library for downloading and caching
images from the web. This project is heavily inspired by the popular SDWebImage.
It provides you a chance to use a pure-Swift alternative in your next app.

Kingfisher 是一个轻量级的，纯 swift 语言的网络图片下载和缓存库。这个项目受到流行
的 SDWebImage 的极大启发。

## 结构：

## protocol:

* KingfisherCompatible

UIImage,UIImageView,UIButton 的扩展`KingfisherCompatible`提供了链式访问`.kf`的扩
展 , 方便访问`Kingfisher`实例。

## Kingfisher

Kingfisher 库的访问类，final 不可继承。

Kingfisher 持有属性`base`，是 UIImage,UIImageView 或者 UIButton 的实例。

## ImageView 扩展

提供了两个扩展方法：

    // 设置网络图片
    public func setImage(with resource: Resource?,
                         placeholder: Placeholder? = nil,
                         options: KingfisherOptionsInfo? = nil,
                         progressBlock: DownloadProgressBlock? = nil,
                         completionHandler: CompletionHandler? = nil) -> RetrieveImageTask
    // 取消下载任务
    public func cancelDownloadTask()

参数：

`Resource`: 图片资源协议，包括图片的`cacheKey`以及`downloadURL`, 提供
了`ImageResource`结构体实现此协议。

`Placeholder`：图片占位符协议，提供了向 `UIImageView` 添加和删除占位符的接口
，`UIImage` 默认实现此协议，经自身设置给 UIImageView

`KingfisherOptionsInfo`:

`DownloadProgressBlock`：下载进程回调 block 闭包

    ((_ receivedSize: Int64, _ totalSize: Int64) -> ())

    回调包含参数`receivedSize`和`totalSize`

`completionHandler`：下载完成回调 block 闭包，

    ((_ image: Image?, _ error: NSError?, _ cacheType: CacheType, _ imageURL: URL?) -> ())

<!-- 回调中包含 -->
