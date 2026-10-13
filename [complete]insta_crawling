import time
from selenium import webdriver
from bs4 import BeautifulSoup
import time
import re
import pandas as pd

# 크롬 브라우저 열기
driver = webdriver.Chrome(executable_path='C:/chromedriver_win32/chromedriver.exe') 

driver.get('https://www.instagram.com')
time.sleep(2)


#아이디 패스워드 입력 
email = 'remdahye@gmail.com' 
input_id = driver.find_elements_by_css_selector('input._2hvTZ.pexuQ.zyHYP')[0]
input_id.clear()
input_id.send_keys(email)

password = 'daddong2@' 
input_pw = driver.find_elements_by_css_selector('input._2hvTZ.pexuQ.zyHYP')[1]
input_pw.clear()
input_pw.send_keys(password)
input_pw.submit()


def finding_postnumber(keyword):
    url = "https://www.instagram.com/explore/tags/" + keyword
    driver.get(url)
    
    time.sleep(2)
    
    
    html = driver.page_source
    soup = BeautifulSoup(html, 'lxml')

    txt = soup.find(class_='_ac2a')
    number = float(txt.text.replace(',', ''))
    
    return number

data_number = []

lists = ["도시설계", "관광"] 
# 데이터 불러오기
# csv_file = pd.read_csv('G:/내 드라이브/0. Data/test.csv', encoding='cp949', engine='python')   
# lists = csv_file["column name(ex-키워드)"]  ; column_name에 칼럼이름 (첫번째 행)

for i in lists:
    a = finding_postnumber(i)
    data_number.append(a)


df = pd.DataFrame({'키워드':lists,'포스팅수':data_number})

df

print(df)


#검색 결과 저장 
# df.to_csv('G:/내 드라이브/주소/파일명.csv')
