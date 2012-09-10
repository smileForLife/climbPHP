climbPHP
========

这是codeIgniter的扩展框架，提供了 “更好的模块化” “广播系统” “实体系统” 这三个主要的扩展功能。

更好的模块化
============
我所指的模块是module，而不是model。model是业务模型，我们能用它进行一定的业务逻辑操作。而模块应该是系统的组成部分，能根据系统事件动态地做出响应。举个简单例子，我有一个普通的日志系统，模块分为日志模块、用户模块。我希望实现在删除用户的时候能同时删除用户的所有日志。仅仅使用CI的model来实现的话，我需要在 “用户model” 中去调用 “日志model” 中的删除方法。而我希望的是用户删除的时候只用考虑自己的逻辑就好了，外部模块会自动进行相应的操作。这样的好处在于，它对任何一个已完成的模块都是“对修改封闭”的。例如我现在增加一个 “关注模块”， 我可以不用再去修改 “用户模块”， 而是在 “关注模块” 中

CI本身并没有实现这样一个模块的机制。所以我自己写了一个。以下简单介绍在climbPHP下如何写一个模块。(以 “用户模块” 为例，实现基本的注册、登陆、删除功能)。

1.