# 什麼是 phantomJS # 

        PhantomJS 是無介面瀏覽器 (Headless browser)，背後的渲染引擎為 WebKit，適合進行自動化測試、捕捉截圖或監測網頁效能。
        因為沒有圖形介面，很容易整合至現有的測試框架，比如 Jasmine、QUnit、Mocha 等等，或是使用基於 PhantomJS 開發的測試框架 CasperJS。
        另一個特點是他能直接控制 DOM，方便你提取網頁中的元素內容，或是使用 JQuery 進行操作。新手上路請參考 PhantomJS 網頁上的 QuickStart，
        以下我們就安裝與網頁截圖的技巧做說明。
參考
- https://jerrynest.io/phantomjs-screenshot/

# Install #

參考 
- https://www.bonusbits.com/wiki/HowTo:Install_PhantomJS_on_CentOS

## bzip2 ##

- yum update
- yum install bzip2

## phantomJS ##

- yum install fontconfig freetype freetype-devel fontconfig-devel libstdc++
- wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.8-linux-x86_64.tar.bz2 --no-check-certificate
- mkdir -p /opt/phantomjs
- bunzip2 phantomjs-1.9.8-linux-x86_64.tar.bz2
- tar xvf phantomjs-1.9.8-linux-x86_64.tar --strip-components=1 -C /opt/phantomjs/
- ln -s /opt/phantomjs/bin/phantomjs /usr/bin/phantomjs

## 字形檔 ##

- yum install cjkuni-* wqy-zenhei-*

- 參考
-- https://note.artchiu.org/2014/05/29/%E5%AE%89%E8%A3%9D-centos-rhel-6-%E9%A0%90%E8%A8%AD%E7%9A%84%E7%B9%81%E9%AB%94%E4%B8%AD%E6%96%87%E5%AD%97%E5%9E%8B%E5%A5%97%E4%BB%B6/
-- https://stackoverflow.com/questions/15029002/phantomjs-screenshot-font-missing-boxes-rendered-instead

## Test ##

- phantomjs /opt/phantomjs/examples/hello.js

## 狀況排除 ##

- Can't install phantomjs on server
-- https://stackoverflow.com/questions/30788858/cant-install-phantomjs-on-server

- Extract tar the tar.bz2 file error
-- https://stackoverflow.com/questions/26958741/extract-tar-the-tar-bz2-file-error
