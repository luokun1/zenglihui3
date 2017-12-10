# zenglihui3
import bs4
import urllib.request
url="https://baike.baidu.com/item/Python/407313?fr=aladdin"
re= urllib.request.urlopen(url)#打开网页
html=re.read()#读取网页
soup = bs4.BeautifulSoup(html, 'lxml')#对读取的网页进行解析
content = soup.find('div', class_='main-content').find('dl', class_='lemmaWgt-lemmaTitle lemmaWgt-lemmaTitle-').find('dd' ,class_="lemmaWgt-lemmaTitle-title")
#缩小范围
try:
    weather = {}
    weather['名称'] = content.find('h1').text#具体区间
    weather['简介'] = content.find('h2').text
except:
    print('查询不到')
print(weather)#输出结果
