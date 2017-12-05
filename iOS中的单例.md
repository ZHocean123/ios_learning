单例存在的意义：保证全局有一个唯一的实例，这样可以满足统一的管理功能。例如数据库
，只需要全局统一的读写操作，不要使用多个实例。

单例只是唯一实例，不代表一直伴随 app 的生命周期

    static Myclass _instance;
    方法一:
    +(id)shareInstance{
      @synchronized(self){
        if(_instance == nil)
          _instance = [MyClass alloc] init];
        }
      return _instance;
    }

    方法二:
    +(id)shareInstance{
      static dispatch_once_t onceToken;
      dispatch_once(&onceToken, ^{
        if(_instance == nil)
          _instance = [MyClass alloc] init];
      });
      return _instance;
    }

以上两种方法都是线程安全的 . 不过苹果官方现在提倡方法二 .

swift 创建单例

    class Myclass {
      let shareInstance = Myclass
    }
