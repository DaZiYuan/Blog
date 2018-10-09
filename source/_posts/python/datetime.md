title: Python 时间运算
author: 打字员
tags:
  - Python
categories:
  - Python
  - ''
  - ''
date: 2018-09-28 17:45:00
---

```Python
import datetime
import time

def wait(timeout_ms, calback=None):
    '''等待指定时间

    Arguments:
        timeout_ms {[type]} -- [等待指定毫秒数]

    Keyword Arguments:
        calback {[type]} -- [每一秒触发一次回调，回调参数是剩余的秒数] (default: {None})
    '''

    now = datetime.datetime.now()
    endTime = now+datetime.timedelta(milliseconds=timeout_ms)
    timespane = endTime-now
    while timespane.seconds > 0:
        if(calback is not None):
            calback(timespane.seconds)
        now = datetime.datetime.now()
        timespane = endTime-now
        time.sleep(1)

def callback(remain_seconds):
    print("剩余", remain_seconds)

wait(5, callback)
print('end')
```

输出结果：
剩余 5
剩余 4
剩余 3
剩余 2
剩余 1
end