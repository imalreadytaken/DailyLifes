- http请求

- 查看已安装的库

  ```shell
  pip list
  ```

### 反射

PyCodeObject源码

```c++
/* Bytecode object */
typedef struct {
    PyObject_HEAD
    int co_argcount;             /* #arguments, except *args */
    int co_kwonlyargcount;       /* #keyword only arguments */
    int co_nlocals;              /* #local variables */
    int co_stacksize;            /* #entries needed for evaluation stack */
    int co_flags;                /* CO_..., see below */
    PyObject *co_code;           /* instruction opcodes */
    PyObject *co_consts;         /* list (constants used) */
    PyObject *co_names;          /* list of strings (names used) */
    PyObject *co_varnames;       /* tuple of strings (local variable names) */
    PyObject *co_freevars;       /* tuple of strings (free variable names) */
    PyObject *co_cellvars;       /* tuple of strings (cell variable names) */
    /* The rest doesn't count for hash or comparisons */
    unsigned char *co_cell2arg;  /* Maps cell vars which are arguments. */
    PyObject *co_filename;       /* unicode (where it was loaded from) */
    PyObject *co_name;           /* unicode (name, for reference) */
    int co_firstlineno;          /* first source line number */
    PyObject *co_lnotab;         /* string (encoding addr<->lineno mapping) See
                                    Objects/lnotab_notes.txt for details. */
    void *co_zombieframe;        /* for optimization only (see frameobject.c) */
    PyObject *co_weakreflist;    /* to support weakrefs to code objects */
} PyCodeObject;
```



```python
if __name__ == '__main__':
    module = 'test_b.test'
    cls = 'Test'
    func = 'key'
    params = {
        'param2': 2,
        'param1': 1,
    }
    # __import__引入模块，fromlist参数不传则只会引入test.b
    f = __import__(module, fromlist= True)
    # 推荐使用这种方式
    f = importlib.import_module(module)
    # 判断给定类/方法是否存在
    print(hasattr(f, cls))
    # 加上()这个之后，r就是一个实例了，可以调用非静态方法，静态方法也可以通过实例来调用
    r = getattr(f, cls)()
    # 或r = r()
    print(hasattr(r, func))
    # 通过反射拿到方法
    b = getattr(r, func)
    # 使用**kwarg的形式更加方便传参
    print(b(**params))
```

## 字典

### 排序

```python
d = {'c' : 'e', 'a': 'd', 'b': 'c'}
sorted_d = dict( sorted(d.items(), key=lambda x:x[0]))
# sorted(d.items(), key=lambda x:x[0]) = [('a', 'd'), ('b', 'c'), ('c', 'e')]，为k,v 的tuple list，然后用dict()方法将其转为字典
```

### 合并

```python
dict_merge = {**dict1, **dict2}
```

### 遍历

```python
a = {'a' : 'sss', 'b' : 'sdfsdf'}
for k,v in a.items():
    print(k,v)
x = [k+'='+v for k,v in a.items()]
print('&'.join(x))
```

## 日志

%(name)s	日志记录器(日志通道)的名称。
%(levelno)s	消息的数字日志级别(DEBUG, INFO, WARNING, ERROR, CRITICAL)。
%(levelname)s	消息的文本日志级别 (‘DEBUG’, ‘INFO’, ‘WARNING’, ‘ERROR’, ‘CRITICAL’)。
%(pathname)s	发出日志调用的源文件的完整路径名 (if available)
%(filename)s	路径名的文件名部分。
%(module)s	模块(文件名的一部分)。
%(funcName)s	包含日志调用的函数的名称。
%(lineno)d	发出日志调用的源代码行号(如果可用)
%(created)f	创建LogRecord的时间 (as returned by time.time()).
%(relativeCreated)d	创建LogRecord的时间(以毫秒为单位)，相对于加载日志模块的时间。
%(asctime)s	创建LogRecord的人类可读时间。默认情况下，这是“2003-07-08 16:49:45,896”(逗号后面的数字是毫秒部分)。
%(msecs)d	创建LogRecord的毫秒部分。
%(thread)d	线程ID(如果可用)。
%(threadName)s	线程名(如果可用)。
%(process)d	进程ID(如果可用)。
%(message)s	日志消息，计算为msg % args。 
作者：Webben 
来源：CSDN 
原文：https://blog.csdn.net/Webben/article/details/83858959 
版权声明：本文为博主原创文章，转载请附上博文链接！

## 其它

### hash

```python
import hashlib
h = hashlib.sha256()
h.update('aaaa'.encode('utf-8'))
print(h.hexdigest())
```



### Python23区别

- JSONDecodeError在2中没有，用ValueError