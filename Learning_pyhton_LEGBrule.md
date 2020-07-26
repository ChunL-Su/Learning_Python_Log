# Python LEGB rule
- 内容来自简书https://www.jianshu.com/p/3b72ba5a209c
- LEGB含义解释
    - L-Local(function):函数内的命名空间
    - E-Enclosing function locals:外部嵌套函数命名空间(例如closure)
    - G-Global(module):函数定义所在模块(文件)的命名空间
    - B-Builtin(Python):Python内置模块的命名空间
- 不同命名空间的优先级
    - Python的命名空间是一个字典，字典内保存了变量名与对象之间的映射关系，因此，查找
      变量名就是在命名空间字典中查找键-值对。Python有多个命名空间，因此，需要有规则来规定，
      LEGB就是用来规定命名空间查找顺序的规则。
    - LEGB规定了查找一个名称的顺序为：local-->enclosing function locals-->global-->builtin
        - 其实就是按照L,E,G,B的这个顺序
        - 例如：
        ```
        x = 1
        def func():
            x = 2
            def innerfunc():
                x = 3
                print('Locals x=', x)
            innerfunc()
            print('Enclosing function locals x=', x)
        func()
        print('Global x=', x)
        ```
