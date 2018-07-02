# Spider_ryan


import re
import urllib.request
def getlink(url):
    #ģ��������
    headers=("User-Agent","Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.122 Safari/537.36 SE 2.X MetaSr 1.0")
    opener = urllib.request.build_opener()
    opener.addheaders = [headers]
    #��opener��װΪȫ��
    urllib.request.install_opener(opener)
    file=urllib.request.urlopen(url)
    data=str(file.read())
    #�������󹹽������ӱ��ʽ
    pat='(https?://[^\s)";]+\.(\w|/)*)'
    link=re.compile(pat).findall(data)
    #ȥ���ظ�Ԫ��
    link=list(set(link))
    return link
#Ҫ��ȡ����ҳ����
url="http://blog.csdn.net/"
#��ȡ��Ӧ��ҳ�а��������ӵ�ַ
linklist=getlink(url)
#ͨ��forѭ���ֱ���������ȡ�������ӵ�ַ����Ļ��
for link in linklist:
    print(link[0])
