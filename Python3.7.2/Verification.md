## Python3

`Python3`

## pip3

`pip3 -v`

## selenium 

`pip3 show selenium`

## dirver

1. Create a new file

```
cd
touch test.py
vim test.py
```

2. Input `i` and copy and paste the following code, press `esc` and enter `:wq`

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

3. Execute python3 file

```
python3 test.py
```

4. View Results

No error is considered success.
