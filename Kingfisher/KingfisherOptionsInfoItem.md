## KingfisherOptionsInfoItem

```swift
/// The associated value of this member should be an ImageCache object. Kingfisher will use the specified
/// cache object when handling related operations, including trying to retrieve the cached images and store
/// the downloaded image to it.
case targetCache(ImageCache)

/// Cache for storing and retrieving original image.
/// Preferred prior to targetCache for storing and retrieving original images if specified.
/// Only used if a non-default image processor is involved.
case originalCache(ImageCache)

/// The associated value of this member should be an ImageDownloader object. Kingfisher will use this
/// downloader to download the images.
case downloader(ImageDownloader)

/// Member for animation transition when using UIImageView. Kingfisher will use the `ImageTransition` of
/// this enum to animate the image in if it is downloaded from web. The transition will not happen when the
/// image is retrieved from either memory or disk cache by default. If you need to do the transition even when
/// the image being retrieved from cache, set `ForceTransition` as well.
case transition(ImageTransition)

/// Associated `Float` value will be set as the priority of image download task. The value for it should be
/// between 0.0~1.0. If this option not set, the default value (`NSURLSessionTaskPriorityDefault`) will be used.
case downloadPriority(Float)

/// If set, `Kingfisher` will ignore the cache and try to fire a download task for the resource.
case forceRefresh

/// If set, `Kingfisher` will try to retrieve the image from memory cache first. If the image is not in memory
/// cache, then it will ignore the disk cache but download the image again from network. This is useful when
/// you want to display a changeable image behind the same url, while avoiding download it again and again.
case fromMemoryCacheOrRefresh

/// If set, setting the image to an image view will happen with transition even when retrieved from cache.
/// See `Transition` option for more.
case forceTransition

///  If set, `Kingfisher` will only cache the value in memory but not in disk.
case cacheMemoryOnly

/// If set, `Kingfisher` will only try to retrieve the image from cache not from network.
case onlyFromCache

/// Decode the image in background thread before using.
case backgroundDecode

/// The associated value of this member will be used as the target queue of dispatch callbacks when
/// retrieving images from cache. If not set, `Kingfisher` will use main quese for callbacks.
case callbackDispatchQueue(DispatchQueue?)

/// The associated value of this member will be used as the scale factor when converting retrieved data to an image.
/// It is the image scale, instead of your screen scale. You may need to specify the correct scale when you dealing
/// with 2x or 3x retina images.
case scaleFactor(CGFloat)

/// Whether all the animated image data should be preloaded. Default it false, which means following frames will be
/// loaded on need. If true, all the animated image data will be loaded and decoded into memory. This option is mainly
/// used for back compatibility internally. You should not set it directly. `AnimatedImageView` will not preload
/// all data, while a normal image view (`UIImageView` or `NSImageView`) will load all data. Choose to use
/// corresponding image view type instead of setting this option.
case preloadAllAnimationData

/// The `ImageDownloadRequestModifier` contained will be used to change the request before it being sent.
/// This is the last chance you can modify the request. You can modify the request for some customizing purpose,
/// such as adding auth token to the header, do basic HTTP auth or something like url mapping. The original request
/// will be sent without any modification by default.
case requestModifier(ImageDownloadRequestModifier)

/// Processor for processing when the downloading finishes, a processor will convert the downloaded data to an image
/// and/or apply some filter on it. If a cache is connected to the downloader (it happens when you are using
/// KingfisherManager or the image extension methods), the converted image will also be sent to cache as well as the
/// image view. `DefaultImageProcessor.default` will be used by default.
case processor(ImageProcessor)

/// Supply an `CacheSerializer` to convert some data to an image object for
/// retrieving from disk cache or vice versa for storing to disk cache.
/// `DefaultCacheSerializer.default` will be used by default.
case cacheSerializer(CacheSerializer)

/// Modifier for modifying an image right before it is used.
/// If the image was fetched directly from the downloader, the modifier will
/// run directly after the processor.
/// If the image is being fetched from a cache, the modifier will run after
/// the cacheSerializer.
/// Use `ImageModifier` when you need to set properties on a concrete type
/// of `Image`, such as a `UIImage`, that do not persist when caching the image.
case imageModifier(ImageModifier)

/// Keep the existing image while setting another image to an image view.
/// By setting this option, the placeholder image parameter of imageview extension method
/// will be ignored and the current image will be kept while loading or downloading the new image.
case keepCurrentImageWhileLoading

/// If set, Kingfisher will only load the first frame from a animated image data file as a single image.
/// Loading a lot of animated images may take too much memory. It will be useful when you want to display a
/// static preview of the first frame from a animated image.
/// This option will be ignored if the target image is not animated image data.
case onlyLoadFirstFrame

/// If set and an `ImageProcessor` is used, Kingfisher will try to cache both
/// the final result and original image. Kingfisher will have a chance to use
/// the original image when another processor is applied to the same resouce,
/// instead of downloading it again.
case cacheOriginalImage
```
