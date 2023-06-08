可以使用NumPy库和Python实现逻辑回归算法。下面是一个示例代码，每行都有详细注释：
逻辑回归算法的详细思路如下：

定义假设函数，即sigmoid函数。
定义损失函数，即交叉熵损失函数。
定义梯度函数，即损失函数对参数的偏导数。
使用梯度下降法或其他优化算法最小化损失函数，得到最优参数。
使用最优参数进行预测。

import numpy as np  # 导入NumPy库

def sigmoid(z):  # 定义sigmoid函数
    return 1 / (1 + np.exp(-z))

def cost_function(theta, X, y):  # 定义损失函数
    m = len(y)  # 样本数量
    h = sigmoid(X @ theta)  # 计算假设函数值
    J = -1 / m * (y.T @ np.log(h) + (1 - y).T @ np.log(1 - h))  # 计算损失函数值
    return J

def gradient(theta, X, y):  # 定义梯度函数
    m = len(y)  # 样本数量
    h = sigmoid(X @ theta)  # 计算假设函数值
    grad = 1 / m * X.T @ (h - y)  # 计算梯度
    return grad

def predict(theta, X):  # 定义预测函数
    p = sigmoid(X @ theta)  # 计算预测值
    return p

def logistic_regression(X, y, theta, alpha, num_iters):  # 定义逻辑回归函数
    m = len(y)  # 样本数量
    J_history = []  # 初始化损失函数值列表
    
    for i in range(num_iters):  # 迭代num_iters次
        theta = theta - alpha * gradient(theta, X, y)  # 梯度下降法更新theta
        J_history.append(cost_function(theta, X, y))  # 记录损失函数值
    
    return theta, J_history  # 返回theta和损失函数值列表
