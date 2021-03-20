## 安装 selenium + chrome + driver


### 安装

```
cd
pip install --upgrade pip
pip install selenium
wget https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm --no-check-certificate
yum install ./google-chrome-stable_current_x86_64.rpm
wget http://chromedriver.storage.googleapis.com/2.43/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
mv chromedriver /usr/bin/
ls
```

### 测试

```
cd
touch test.py
vim test.py
```

```
from selenium import webdriver
url='http://bing.com'
option = webdriver.ChromeOptions()
option.add_argument('--no-sandbox')
option.add_argument('--headless')
driver = webdriver.Chrome(chrome_options=option)
driver.get(url)
print(driver.page_source)
```

```
python test.py
```

```
rm -f test.py
```