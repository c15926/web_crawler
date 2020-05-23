import requests
from bs4 import BeautifulSoup

def get_subjects():
  subjects = []

  #  전체 주제 목록을 보여주는 페이지로의 요청 객체를 생성합니다.

  req = requests.get('https://search.shopping.naver.com/best100v2/detail.nhn?catId=50000000')

  html = req.text
  soup = BeautifulSoup(html, 'html.parser')


  links = soup.select('p > a')

  i = 1
  for link in links:
    # 링크가 href 속성을 가지고 있다면
    if link.has_attr('href'):
      # href 속성의 값으로 000라는 문자열이 포함되어 있다면, 
      if link.get('href').find('cr2.shopping.naver.com') != -1:
        print("(" + repr(i) + "/" + repr(len(links)) + ")" + repr(link.text))
        subject = link.text
        subjects.append(subject)
        i = i + 1
  return subjects

subjects = get_subjects()
print('총 ', len(subjects), '개의 주제를 찾았습니다.')
print(subjects)

