1、广义线性模型是机器学习算法中非常重要的一类模型，可以用于分类、回归等多种任务。广义线性模型假设输出变量y服从指数分布族，同时假设特征和输出变量之间的关系可以用一个线性组合来表示。这个线性组合通过一个链接函数将其映射到指数分布族中的参数空间，从而使模型具有非常广泛的适用性和可解释性。

2、标准的SVM是一种二分类模型，可以使用核方法将数据映射到高维空间中，从而找到一个最优分类面来区分两类数据。在实际应用中，后验概率是非常有用的，因为它可以告诉我们每个样本属于每一类的概率，这对于一些任务比如风险评估非常有帮助。

要实现SVM的后验概率输出，有两种常用的方法。第一种方法是使用Platt Scaling，该方法通过在SVM的输出结果上再拟合一个逻辑回归模型来实现后验概率输出。第二种方法是使用直接优化后验概率的SVM方法，例如SVMlight和LIBSVM中的Probabilistic SVM方法。这些方法在训练SVM的同时，通过加入先验概率和极大似然估计来直接优化后验概率的输出。

广义线性模型是一种广泛应用于机器学习的模型，其通过对线性模型进行扩展和泛化，可以适用于更广泛的数据类型和应用场景。广义线性模型可以用于回归问题和分类问题，并且可以处理二元和多元分类问题。其中，Logistic回归、softmax回归和线性判别分析等算法都是广义线性模型的典型应用。

在标准的SVM中，样本被分为+1或-1，但在实际应用中，我们往往需要得到样本属于某一类别的后验概率，以便进行更精细的分类决策或者风险控制。为了使SVM能够输出后验概率，通常有以下两种方法：

Platt缩放法：该方法通过在SVM输出值上训练一个sigmoid函数，将输出值映射到[0,1]区间内，从而得到后验概率。具体实现中，需要使用交叉验证的方法确定sigmoid函数的参数，以避免过拟合。
直接优化后验概率：该方法通过修改SVM的目标函数，引入一个正则化项来约束模型复杂度，从而使模型更稳健。通过将后验概率引入到目标函数中，可以直接优化后验概率。具体实现中，需要使用一些优化算法来求解最优参数。

#Write afunction solution that, given an array A consisting of N integers, returns the number of fragments of A whose sum equals 0 (that is, pairs(P Q) such that P ≤Q and the sum A[P]+A[P+1]+.…. + A[Q] is 0). The function should return -1 if this number exceeds 1,000,000,000.
Examples:
1. GivenA=[2,-2,3,04,-7],the function should return 4, as explained on this picture:

2. Given A =[0,o, 0] of length 100,000, the function should return -1.
Write an efficient algorithm for the following assumptions:
N is an integer within the range [1..100,000];
each element of array A is an integer within the range test

https://www.google.com/appserve/mkt/p/AFnwnKUFNcRXfxJ0cOyyf63xlfpXiago9Awjad9AuZvxgn8lJJcyONGXEP4OpZGqxJf2IphKFeGDMBs1ZSi3ljheqbDQ_lVN4j3eA8XXP_fTbK97G0BJeoycScpHO9VBpivxDaUdd2KN3DlVJteBzHMInFA1gSVBu9XW_c4Eb2SqcgmSNSl-5_rrFK_jRrmwn_dKHz-QMZclPgs6o8o0W98bSb6VXX2ry-0P7Mno-EZcn8CTzp5e-Xi1F2JKCNMbOAxF5zO1XTYoo-mdrZbEwK-j5JZ0Hf-C83ZUong_7vD3-xBS3R91Ls5eMmZivi_5cLcN2kuf2Yj-


https://www.google.com/appserve/mkt/p/AFnwnKUFNcRXfxJ0cOyyf63xlfpXiago9Awjad9AuZvxgn8lJJcyONGXEP4OpZGqxJf2IphKFeGDMBs1ZSi3ljheqbDQ_lVN4j3eA8XXP_fTbK97G0BJeoycScpHO9VBpivxDaUdd2KN3DlVJteBzHMInFA1gSVBu9XW_c4Eb2SqcgmSNSl-5_rrFK_jRrmwn_dKHz-QMZclPgs6o8o0W98bSb6VXX2ry-0P7Mno-EZcn8CTzp5e-Xi1F2JKCNMbOAxF5zO1XTYoo-mdrZbEwK-j5JZ0Hf-C83ZUong_7vD3-xBS3R91Ls5eMmZivi_5cLcN2kuf2Yj-

https://www.google.com/appserve/mkt/p/AFnwnKUFNcRXfxJ0cOyyf63xlfpXiago9Awjad9AuZvxgn8lJJcyONGXEP4OpZGqxJf2IphKFeGDMBs1ZSi3ljheqbDQ_lVN4j3eA8XXP_fTbK97G0BJeoycScpHO9VBpivxDaUdd2KN3DlVJteBzHMInFA1gSVBu9XW_c4Eb2SqcgmSNSl-5_rrFK_jRrmwn_dKHz-QMZclPgs6o8o0W98bSb6VXX2ry-0P7Mno-EZcn8CTzp5e-Xi1F2JKCNMbOAxF5zO1XTYoo-mdrZbEwK-j5JZ0Hf-C83ZUong_7vD3-xBS3R91Ls5eMmZivi_5cLcN2kuf2Yj-

https://careers.google.com/jobs/results/4683855741255680/

-----------------------

https://docs.google.com/forms/d/e/1FAIpQLSexUMuljGTy_o6hzLaorbFPllOv1sdg2f5mlgjbWWRs4lgp2g/viewform?entry.581279853=960629123
