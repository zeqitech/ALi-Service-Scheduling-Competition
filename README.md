# 解决方案逻辑流程及算法详情
## 解决方案逻辑流程
### 基本思路：

让专家去挑选任务，而不是让任务去挑选专家，这样相比较于我们最初的任务选专家，响应超时和负荷有着明显地下降。

### 流程说明

1. 首先让专家去挑选能够及时响应的任务（任务来了就开始处理，不需要等待）
2. 循环多次，让那些负荷少的专家增加他们的负荷。
3. 让专家去挑选那些需要等待的任务，选择引起整体时延最短的专家去处理，如果新任务与原有任务有冲突，则让新任务插入，原有任务往后挪动。
4. 循环直到分配完所有任务。

流程图说明：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201018155249311.png)

---

## 算法详情
### 对于无时延处理的任务
在第一次处理中，我们对每个专家的技能进行了一次排序，让专家能够去处理他最擅长的任务。
之后的循环中，我们优先处理负荷最小的专家，增加这些专家的负荷。

### 对于存在时延的任务
我们选择插入当前任务会照成整体时延最少的专家进行处理，插入方法为，从该任务能插入进去的时间点分配该任务，如果与后面的任务冲突，则让后面的任务按时间往后挪动，知道任务能够无冲突的插入。

---

# 代码运行说明

python main.py  

相关依赖包：numpy
