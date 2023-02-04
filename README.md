# homework..
#1
def test_distinct(data):
  if len(data) == len(set(data)):
    return True
  else:
    return False;
print(test_distinct([1,5,7,9]))
print(test_distinct([2,4,5,5,7,9]))
#2
import random
char_list = ['a','e','i','o','u']
random.shuffle(char_list)
print(''.join(char_list))
#3
def remove_nums(int_list):
  #list starts with 0 index
  position = 3 - 1
  idx = 0
  len_list = (len(int_list))
  while len_list>0:
    idx = (position+idx)%len_list
    print(int_list.pop(idx))
    len_list -= 1
nums = [10,20,30,40,50,60,70,80,90]
remove_nums(nums)
#4
def three_sum(nums):
  result = []
  nums.sort()
  for i in range(len(nums)-2):
    if i> 0 and nums[i] == nums[i-1]:
      continue
    l, r = i+1, len(nums)-1
    while l < r:
      s = nums[i] + nums[l] + nums[r]
      if s > 0:
        r -= 1
      elif s < 0:
          l += 1
      else:
        # found three sum
        result.append((nums[i], nums[l], nums[r]))
        # remove duplicates
        while l < r and nums[l] == nums[l+1]:
          l+=1
          while l < r and nums[r] == nums[r-1]:
            r -= 1
            l += 1
            r -= 1
          return result

x = [1, -6, 4, 2, -1, 2, 0, -2, 0 ]
print(three_sum(x))
#5
numbers = []
for num in range(1000):
  num=str(num).zfill(3)
print(num)
numbers.append(num)
#6
string_words = '''Advanced English reading texts: while the majority of texts in this resource are at CEF levels C1,  
a few are harder (level C2) and a few are easier (level B2). All the texts in this collection are written in normal English; 
however in order to maximize their language  teaching potential, most have been specifically written for students of English 
as a foreign or second language, or else for high school students. Texts are accompanied by advanced reading comprehension 
worksheets designed to prepare students for the Cambridge
Advanced English (C1) certification or for the international  TOEFL or TOEIC tests. Printable reading texts: most pages 
are printer-friendly and will print directly as well as, or better than, PDF versions.'''
word_list = string_words.split()
word_freq = [word_list.count(n) for n in word_list]
print("String:\n {} \n".format(string_words))
print("List:\n {} \n".format(str(word_list)))
print("Pairs (Words and Frequencies:\n {}".format(str(list(zip(word_list, word_freq)))))
#7
import collections
import pprint
file_input = input('File Name: ')
with open(file_input, 'r') as info:
  count = collections.Counter(info.read().upper())
  value = pprint.pformat(count)
print(value)
#8
import bs4
from bs4 import BeautifulSoup as soup
from urllib.request import urlopen

news_url="https://news.google.com/news/rss"
Client=urlopen(news_url)
xml_page=Client.read()
Client.close()

soup_page=soup(xml_page,"xml")
news_list=soup_page.findAll("item")
for news in news_list:
  print(news.title.text)
  print(news.link.text)
  print(news.pubDate.text)
  print("-"*60)
#9
import pkg_resources
installed_packages = pkg_resources.working_set
installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
for m in installed_packages_list:
    print(m)
#10
import platform as pl
os_profile = [
        'architecture',
        'linux_distribution',
        'mac_ver',
        'machine',
        'node',
        'platform',
        'processor',
        'python_build',
        'python_compiler',
        'python_version',
        'release',
        'system',
        'uname',
        'version',
    ]
for key in os_profile:
  if hasattr(pl, key):
    print(key +  ": " + str(getattr(pl, key)()))
