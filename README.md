##学习成绩的程序设计 12.13
with open('roll_book.csv') as fp:
    print(fp.read())
with open('roll_book.csv') as fp:
    for line in fp:
        line=line.split(',')
        print(line)
with open('roll_book.csv') as fp:
    for line in fp:
        line=line.split(',')
        print('{} {} {} {}'.format(line[0],line[1],line[2],line[3]),end='')

def max_min_avg(score):
    max_=max(score)
    min_=min(score)
    avg_=sum(score)/len(score)
    return(max_,min_,avg_)

#绘出分数段图
import matplotlib.pyplot as plt
def histogram(scores,start=30,sep=10):
    hist={}
    for i in range(start,101,sep):
        hist[i]=0
    for i in scores:
        t=(i+10)-(i%10)
        hist[t]+=1
    values=hist.values()
    plt.figure(figsize=(6,5))
    plt.bar(range(start,101,sep),values,width=5,color='red')
    plt.show()

def analysis(file):
    with open(file) as fp:
        math,physics=[],[]
        fp.readline()
        for line in fp:
            line=line.split(',')
            math.append(int(line[3]))
            tmp=line[3].split('\n')
            physics.append(int(tmp[0]))
        max_,min_,avg_=max_min_avg(physics)
        print('数学最高分：',max_)
        print('数学最低分：',min_)
        print('数学平均分：{:.2f}'.format(avg_))
        max_,min_,avg_=max_min_avg(physics)
        print('物理最高分：',max_)
        print('物理最低分：',min_)
        print('物理平均分：{:.2f}'.format(avg_))
        histogram(math)
        histogram((physics))
analysis('roll_book.csv')
