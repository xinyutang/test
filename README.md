好的，这是每行代码的详细注释：

```python
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
```

: https://www.w3schools.com/python/python_ml_logistic_regression.asp
: https://docs.python.org/3/tutorial/index.html
: https://www.w3schools.com/python/
