# Selenium installation

Selenium can test websites without manually clicking on buttons.

## Install webdrivers

```
# Install Chrome webdriver for 64bit GNU/Linux
wget https://chromedriver.storage.googleapis.com/2.32/chromedriver_linux64.zip
unzip chromedriver_linux64.zip
cp chromedriver /usr/local/bin

# Install Firefox webdriver for 64bit GNU/Linux
wget https://github.com/mozilla/geckodriver/releases/download/v0.19.0/geckodriver-v0.19.0-linux64.tar.gz
tar zxvf geckodriver-v0.19.0-linux64.tar.gz
cp geckodriver /usr/local/bin
```
