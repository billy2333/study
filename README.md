# study
学习专用
def count_char(file):
    dic={}
    with open(file) as fp:
        a=fp.read().replace(' ','').replace('\n','')
        for item in a:
            if item in dic:
                dic[item]+=1
            else:
                dic[item]=1
        l=list(dic.items())
        l=sort(key=lambda x:x[1],reverse=True)
        for i in range(5):
            print(l[i])
count_char('data.txt')

def wc(file):
    dic={}
    with open(file) as fp:
        a=fp.read().replace('\n','')

        for item in a:
            if item in dic:
                dic[item]+=1
            else:
                dic[item]=1
        l=list(dic.items())
    l.sort(key=lambda x:x[1],reverse=True)
    for i in range(5):
        print(l[i])
