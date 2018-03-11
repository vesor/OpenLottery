# 公司抽奖
一个真正去中心化的实现需要参与者具有一定的相关知识，在具体实践中，我们必须权衡公平和效率。
## 身份认证
可使用公司邮箱作为身份认证。
## 操作步骤
1）员工使用公司邮箱将hash(LuckyNumber)发送到指定邮箱地址（比如lucky@mycompany.com)
2）公司管理员汇总所有hash(LuckyNumber)，确认参与者资格（比如某些人不参与抽奖），参与者票数（比如带家属的有2票），
去除重复参与（比如一个人有多个邮箱地址）。汇总后的总表以 邮箱地址/hash(LuckyNumber) 的形式发送给所有人。
3）员工检查总表信息，确认无误后进入下一阶段：发送LuckyNumber到指定邮箱地址。
4）管理员汇总所有LuckyNumber，确定所有LuckyNumber的hash值与之前发送的hash(LuckyNumber)相同。
汇总后的总表以 邮箱地址/hash(LuckyNumber)/LuckyNumber 的形式发送给所有人。
5）管理员（以及所有人）计算LuckyNumber之和SumOfLuckyNumber，然后计算每一个LuckyNumber/SumOfLuckyNumber的hash值，
对hash值进行排序，得到有序列表。前N个即为中奖者。
6）重复上述步骤可再次抽奖。
