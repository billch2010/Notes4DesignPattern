# 单例模式 Singleton Pattern
该模式是相对简单容易理解的一种设计模式。全局希望只生成一个对象，例如一些资源管理、线程池、注册表、日志管理等对象。定义：确保一个类只有一个实例，并提供一个全局访问点。

好处：可延迟实例化，尤其对于那些必要时才需要创建对象且初始化复杂的类，可将实例的创建耗时延迟到实际需要的时刻。

注意点：1. 多线程问题；2.构造函数私有化，避免重复构造；

经典实现：
- 1.急切实例化
```
Class Singleton {
  public:
    static Singleton* GetInstance() {
      if (!instance) instance = new Singleton();
      return instance;
    }
  private:
    Singletone() {}
    static Singleton* instance;
};
Singleton::instance = new Singleton();
```
- 2.延迟实例化
```
Class Singleton {
  public:
    static Singleton* GetInstance() {
      static Singleton instance;
      return &instance;
    }
  private:
    Singletone() {}
};
```
