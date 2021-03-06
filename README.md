# FlaskDemo
Using Flask to build web

## 資料夾結構：
### \*<span style="color:blue;">必須要有正確的結構，Flask才能抓取到頁面檔案</span>\*
## 1. 沒有使用Package（Teacher's case)  
    /FlaskDemo
        /templates (html或其他種類的頁面檔案，此為render_template預設尋找檔案的路徑)
            index.html
        /static (可以把CSS, Javascript放在這個資料夾)
        /env (虛擬環境)
        Hello_Flask.py
      
## 2. 有使用Package  
    /FlaskDemo
        /Package
            /__init__.py  （這個檔案一定要有，應是Python用來識別此區塊內的檔案都屬於此Package，裡面的程式碼空白沒關係)
            /templates (html或其他種類的頁面檔案，此為render_template預設尋找檔案的路徑)
                /index.html
            /static (可以把CSS, Javascript放在這個資料夾)
            /Hello_Flask.py
            /env (虛擬環境)

P.S.此範例資料夾結構為第一種

執行步驟：
> 1. 由於目前flask只有安裝在虛擬環境，所以要進入到正確的虛擬環境內，以此專案為例，必須進入../FlaskDemo/env/bin/ 執行 activate (windows和mac啟用指令不同) , Console下達指令及結果如下：

            MacBook-Pro-2:FlaskDemo ken$ source env/bin/activate
            (env) MacBook-Pro-2:FlaskDemo ken$
        
> 2. 確認進入虛擬環境後執行撰寫好的主程式。 Windows : python Hello_Flask.py   Mac: python3 Hello_Flask.py （示意執行方式，要注意指到對的路徑) , Console下達指令及結果如下：（執行成功的話會看到以下 Running on ..... 的訊息)

            (env) MacBook-Pro-2:FlaskDemo ken$ python3 Hello_Flask.py
            Running on http://127.0.0.1:8080/ (Press CTRL+C to quit)
            Restarting with stat
            Debugger is active!
            Debugger PIN: 280-562-887

> 3. 驗證執行結果，於瀏覽器輸入 http://127.0.0.1:8080/hello (此範例為此路徑，個人可自行設定，詳情見Hello_Flask.py)
![替代文字](https://github.com/tsunglinken/FlaskDemo/blob/master/doc/hello.png "選擇文字")

## Flask與Leveldb搭配使用：
> 1. Leveldb 只能一次一個process使用，被使用的狀態下是被鎖定的，所以當使用flask app.run時，就會造成db lock問題

> 2. 只要能夠避免不要同時間有多個process同時執行即可避免此問題(不確定這樣解釋好不好)

> 3. 具體解決方式： 將資料庫的操作和啟動Flask的行為分開，不同時進行即可。