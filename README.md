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
