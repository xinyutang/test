
Transformer的位置编码方式不能处理变长输入序列，而BERT需要更多的计算资源和更多的训练数据。这是它们各自的缺点。

BERT和Transformer的位置编码方式是不同的。在Transformer中，位置编码是通过将位置信息编码为一个向量，然后将其添加到输入嵌入中来实现的。而在BERT中，位置编码是通过将位置信息编码为一个向量，然后将其与token嵌入相加来实现的。这种方法可以避免在输入嵌入中添加位置编码向量时出现的信息丢失问题。

关于优缺点，Transformer的优点是可以并行计算，而且可以处理任意长度的序列。但是，它不能处理变长输入序列。而BERT可以处理变长输入序列，并且可以在不同任务之间共享参数，从而提高模型效率。但是，BERT需要更多的计算资源和更多的训练数据。


BERT和Transformer的位置编码方式是不同的。在Transformer中，位置编码是通过将位置信息编码为一个向量，然后将其添加到输入嵌入中来实现的。而在BERT中，位置编码是通过将位置信息编码为一个向量，然后将其与token嵌入相加来实现的。这种方法可以避免在输入嵌入中添加位置编码向量时出现的信息丢失问题。


你可以使用文本匹配算法，如余弦相似度、Jaccard相似度等，来计算query和库里面所有问题的相似度，然后根据相似度排序，选出相似度最高的前几个问题。如果你想要更高的精度，可以使用深度学习模型，如BERT、RoBERTa等。¹²³

希望这能帮到你。

Source: Conversation with Bing, 6/8/2023(1) 搜索中的深度匹配模型（下） - 知乎 - 知乎专栏. https://zhuanlan.zhihu.com/p/118183738 Accessed 6/8/2023.
(2) FAQ检索式问答系统及文本匹配计算 - 知乎 - 知乎专栏. https://zhuanlan.zhihu.com/p/79698318 Accessed 6/8/2023.
(3) 基于规则的query分析 - 简书. https://www.jianshu.com/p/1d5a4ae490c1 Accessed 6/8/2023.

import math

# 计算一次表达式的值
def calculate(expr):
    # 先将字符串中的加减乘除符号替换为Python的数学运算符
    # eval函数可以直接计算字符串表达式的值
    # 注意：使用eval存在一定的安全隐患，实际应用中应该谨慎使用
    expr = expr.replace('+', '+').replace('-', '-').replace('*', '*').replace('/', '/')
    return eval(expr)

# 处理一次操作
def process_op(nums, ops, idx, op):
    # 将指定位置的加号替换为指定的加减乘除符号
    ops[idx] = op
    # 构造新的表达式
    expr = ""
    for i in range(len(nums)):
        if i > 0:
            expr += ops[i-1]
        expr += str(nums[i])
    # 计算表达式的值，并四舍五入保留一位小数
    return round(calculate(expr), 1)

# 处理多次操作
def process_ops(nums, ops, ops_list):
    # 记录每次操作的结果
    results = []
    # 逐次处理每次操作
    for i in range(len(ops_list)):
        idx, op = ops_list[i]
        # 处理一次操作并记录结果
        result = process_op(nums, ops, idx-1, op)
        results.append(result)
    return results

# 读入数据
n = int(input())
nums = list(map(int, input().split()))
m = int(input())
ops = ['+'] * (n-1)
ops_list = []
for i in range(m):
    idx, op = input().split()
    ops_list.append((int(idx), op))

# 处理多次操作
results = process_ops(nums, ops, ops_list)

# 输出结果
for result in results:
    print(result)
