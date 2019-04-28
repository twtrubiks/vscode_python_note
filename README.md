# Python in Visual Studio Code

這篇文章將會教大家如何建立自己的 Visual Studio Code Python 開發環境 📝

* [Youtube - Visual Studio Code Python 基本設定篇](https://youtu.be/tS4beaq9ies)

## 說明

最近剛好接觸到使用 VSCode 開發 Python，所以就有了這篇文章:smile:

其實我之前都是使用 Pycharm Professional 來開發的 ( 雖然他要付費，但是功能真的強:+1:)

如果想當免費仔，可以使用 VSCode，但我覺得需要稍微設定一下 ( 這篇文章會教大家 )。

請先準備以下的功課

* 安裝 python 以及 Visual Studio Code

## 步驟一 - 建立 virtual environments

首先，別急著打開 VSCode，先來建立環境，如果你不知道如何建立環境，

可參考這篇文章 [python venv 建立 virtual environments](https://github.com/twtrubiks/python-creation-of-virtual-environments)

( 以前我教過大家 [使用 Anaconda 建立 Python 環境](https://github.com/twtrubiks/FaceDetect/tree/master/How%20Easy%20Install%20OpenCV%20%20for%20Python%20use%20Anaconda#%E4%BD%BF%E7%94%A8-anaconda-%E5%BB%BA%E7%AB%8B-python-%E7%92%B0%E5%A2%83)，但因為 Anaconda 實在很肥，

如果沒有特別的需求，使用 python venv 即可 )

這邊就先建立一個 venv_demo 的環境，

![alt tag](https://i.imgur.com/cmxKh9A.png)

## 步驟二 - 設定 VSCode

這邊為了方便後續的說明，先建立一個資料夾，資料夾名稱 demo，裡面新增一個 demo.py 的檔案，

開啟的方式很多種，這邊直接右鍵開啟，

![alt tag](https://i.imgur.com/WzkoCTN.png)

打開後，快捷鍵 `Ctrl+Shift+P`，然後輸入 settings

![alt tag](https://i.imgur.com/HT7YSDt.png)

主要先看這兩個即可，分別是

Preferences: Open User Settings : 你可以簡單把他想成是全域的。

Preferences: Open Workspace Settings : 只在你的工作目錄內才會生效 ( 工作目錄內會多出一個資料夾 )。

這邊我們先選擇 Preferences: Open User Settings，

這邊是 ui 的呈現 ( 可直接在這邊修改 )，但我喜歡用 json 的方式，點選右邊

![alt tag](https://i.imgur.com/ajFzQM2.png)

這裡面有可能有你自己的設定，這邊是我自己的設定，大家可以參考一下，

![alt tag](https://i.imgur.com/2xVqcFS.png)

```json
{
    // User Settings

    "window.zoomLevel": 1, // 視窗縮放
    // "editor.fontSize": 22,
    // "editor.lineHeight": 26,    
    // "terminal.integrated.fontSize": 30, // terminal 字體大小
    // "editor.formatOnSave": true, // 當儲存時，是否自動格式化
    "files.autoSave": "onFocusChange", // 是否自動儲存檔案

    // 注意，win 用戶都要使用 "\\"
    "python.pythonPath": "C:\\Users\\twtru\\Anaconda3\\envs\\venv_temp\\python.exe", // 預設的 PYTHON 執行環境

    "extensions.ignoreRecommendations": true, // 是否忽略顯示建議的套件
    "files.encoding": "utf8", // 設定預設編碼
    "files.trimTrailingWhitespace": true, // 儲存的時候，會幫你自動過濾多餘的空格
    "files.autoGuessEncoding": false, // 是否自動猜測檔案的編碼
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\cmd.exe",
    // "workbench.welcome.enabled": false, // 使否關閉 vscode 歡迎的顯示頁面
    "workbench.startupEditor": "newUntitledFile",
    "explorer.confirmDelete": false,

    // "workbench.colorTheme": "One Dark Pro", // 需安裝 One Dark Pro
    "workbench.iconTheme": "vscode-icons",  // 需安裝 vscode-icons
}
```

( 其實 json 是不適合註解的，所以才會變成這樣，但不註解我怕大家不了解 )

儲存後就會生效。

也不用擔心亂輸入或輸入錯了會造成什麼問題，如果你打錯字或沒這個東西，VSCode 會提醒你。

接著選擇 Preferences: Open Workspace Settings，

你會發現目錄資料夾底下多了一個 `\.vscode\settings.json` ( 因為這是 Workspace Settings )

![alt tag](https://i.imgur.com/pKDNYP9.png)

這邊是我自己的設定，大家可以參考一下，

![alt tag](https://i.imgur.com/Bm1Foe7.png)

```json
{
    // Workspace Settings
    
    // virtual environments 中的 python 執行檔
    "python.pythonPath": "C:\\Users\\twtru\\OneDrive\\work\\venv\\venv_demo\\Scripts\\python.exe",
    
    // 可以設定你放全部的 venvs 環境的根目錄資料夾
    "python.venvPath": "C:\\Users\\twtru\\OneDrive\\work\\venv",
    
    "python.terminal.activateEnvironment": true, // 自動啟動環境
    "python.linting.pylintEnabled": true,  // 需要 pip install pylint
    "python.linting.enabled": true,  // 需要 pip install pylint
}
```

( 其實 Workspace Settings 這邊的設定，除了 python.pythonPath 之外，都可以搬到 User Settings 裡面)

如果你的 python.venvPath 有設定對，你看你的左下角

![alt tag](https://i.imgur.com/PBo2ab0.png)

選他你會看到資料夾裡面全部的 venv，點了就可以啟動。

![alt tag](https://i.imgur.com/qn1xVM2.png)

( 如果看不到，請重新打開 VSCode，另外要 **注意 Workspace Settings 會覆蓋 User Settings** )

linting 有很多種，這邊選擇 pylint，更多資訊可參考 [Linting Python in Visual Studio Code](https://code.visualstudio.com/docs/python/linting)，

儲存完畢後，快捷鍵 Ctrl+Shift+` 開啟 terminal，

你會發現環境自動啟動了 ( 看前面的小括號 venv_demo )。

( 另外一點要注意的是，VSCode 是偵測你有沒有 .py 的檔案，所以記得要在 .py 的檔案下 Ctrl+Shift+` 開啟 terminal，

否則你會覺得很怪，一直無法自動啟動環境 )

( 如果沒有啟動，可以關掉目前的 terminal 再開一個 terminal 試試看，如果還是不行，關掉 VSCode 重開，

再不行，檢查是不是設定錯了  )

![alt tag](https://i.imgur.com/av5XtVK.png)

大家應該有發現右下角告訴我們沒安裝 pylint ，這時候請安裝 `pip install pylint`

![alt tag](https://i.imgur.com/HCPyLlJ.png)

也可以 快捷鍵 `Ctrl+Shift+P`，然後輸入 linting 檢查一下

![alt tag](https://i.imgur.com/5V1BoUj.png)

會是 on 的狀態，因為設定了 `"python.linting.enabled": true`

![alt tag](https://i.imgur.com/sX4vqc9.png)

## 結論

基本上 VSCode 可以設定的東西真的非常的多，大家可以自行摸索。:relaxed:

這篇是教大家一些很基本的設定，未來如果有機會，再介紹更多的功能給各位認識。

## Donation

文章都是我自己研究內化後原創，如果有幫助到您，也想鼓勵我的話，歡迎請我喝一杯咖啡:laughing:

![alt tag](https://i.imgur.com/LRct9xa.png)

[贊助者付款](https://payment.opay.tw/Broadcaster/Donate/9E47FDEF85ABE383A0F5FC6A218606F8)

## License

MIT license
