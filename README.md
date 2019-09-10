# Dice-Rolls（刷爆难题-8）
### 某厂笔试题复盘，好像是拼多多，记不太清了
掷n个不同面数的骰子，以最大点数为结果，求点数的期望。

一共有n个骰子

第i个骰子面数为ni，点数为[1,ni]，每个面的概率相同

同时掷这n个骰子，得到的最大点数为最终点数

求最终可能的所有点数的概率，保留两位小数

## code

    n=int(input())
    xi=list(map(int,input().split()))
    xi.sort(reverse=True)
    res=[0]
    current=[0]
    for i in range(xi[0]):
        res.append(1/xi[0])
        current.append(1/xi[0])
    print(res)
    for i in range(1,n):
        for j in range(1,xi[i]+1):
            print(res)
            a=sum(res[:j])*(1/xi[i])
            b=res[j]*((j-1)/xi[i])
            c=res[j]*(1/xi[i])
            print(a,b,c)
            current[j]=a+b+c
        for i in range(1,xi[i]+1):
            res[i]=current[i]
    print(res)
    ac=0
    for i in range(1,len(res)):
        ac+=i*res[i]
    print(ac*100//1/100)


