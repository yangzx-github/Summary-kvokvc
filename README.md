# Summary-kvokvc
键值观察（Key-value observing，或简称 KVO）允许对象观察另一个对象的属性。
KVO是Cocoa的一个重要机制，他提供了观察某一属性变化的方法，极大的简化了代码。这种观察－被观察模型适用于这样的情况，比方说根据A（数据类）的某个属性值变化，B（view类）中的某个属性做出相应变化。对于推崇MVC的cocoa而言，kvo应用的地方非常广泛。
适用kvo时，通常遵循如下流程：
1 注册：
-(void)addObserver:(NSObject *)anObserver forKeyPath:(NSString *)keyPath options:(NSKeyValueObservingOptions)options context:(void *)context
keyPath就是要观察的属性值，options给你观察键值变化的选择，而context方便传输你需要的数据（注意这是一个void型）
2 实现变化方法：
-(void) observeValueForKeyPath:(NSString *)keyPath ofObject:(id)object
change:(NSDictionary *)change context:(void *)context
change里存储了一些变化的数据，比如变化前的数据，变化后的数据；如果注册时context不为空，这里context就能接收到。
是不是很简单？kvo的逻辑非常清晰，实现步骤简单。
说了这么多，大家都要跃跃欲试了吧。可是，在此之前，我们还需要了解KVC机制。其实，知道了kvo的逻辑只是帮助你理解而已，要真正掌握的，不在于kvo的实现步骤是什么，而在于KVC，因为只有符合KVC标准的对象才能使用kvo（强烈推荐要使用kvo的人先理解KVC）。
