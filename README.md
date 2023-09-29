# Python in Visual Studio Code

這篇文章將會教大家如何建立自己的 Visual Studio Code Python 開發環境 📝

* [Youtube - Visual Studio Code Python 基本設定篇](https://youtu.be/tS4beaq9ies)

* [Youtube - Visual Studio Code Python Importmagic - Auto import,complete](https://youtu.be/5MgvnPKfrMg)

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
    //"python.defaultInterpreterPath": "C:\\Users\\twtru\\Anaconda3\\envs\\venv_temp\\python.exe", // 預設的 PYTHON 執行環境

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

( `python.defaultInterpreterPath` 這個其實不用另外設定，已註解掉 )

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
    // "python.defaultInterpreterPath": "C:\\Users\\twtru\\OneDrive\\work\\venv\\venv_demo\\Scripts\\python.exe",

    // 可以設定你放全部的 venvs 環境的根目錄資料夾
    "python.venvPath": "C:\\Users\\twtru\\OneDrive\\work\\venv",

    "python.terminal.activateEnvironment": true, // 自動啟動環境
    "python.linting.pylintEnabled": true,  // 需要 pip install pylint
    "python.linting.enabled": true,  // 需要 pip install pylint
}
```

( `python.defaultInterpreterPath` 這個其實不用另外設定，已註解掉 )

( 其實 Workspace Settings 這邊的設定，都可以搬到 User Settings 裡面)

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

如果成功設定,

在 problems 底下會有很多提醒 ( code 會有一些毛毛蟲 )

![alt tag](https://i.imgur.com/ETFCjBX.png)

( 如果一直沒正確啟用 pylint, 可以重新開啟 vscode 或檢查安裝環境 )

也可以新增 `.pylintrc` 設定一些過濾

```text
[MASTER]
# Exclude specific files or directories (comma-separated)
# ignore=.vscode/*,/test/src/tests/*
# ignore-patterns=**/test/src/tests/*.py

[pylint.messages_control]
disable = C0115,C0116,C0115,W0718
```

## Importmagic

* [Youtube - Visual Studio Code Python Importmagic - Auto import,complete](https://youtu.be/5MgvnPKfrMg)

一定有人問 VScode 是否有 auto Import 以及 auto complete 的功能:smile:

Vscode 原生是不支援 auto Import 而且不完整，

這些功能其實需要搭配 [Importmagic](https://marketplace.visualstudio.com/items?itemName=brainfit.vscode-importmagic&fbclid=IwAR2WIhgRxvxeCv3vEGDc56dDQp2idFuDCDPgDqF2vXAiF7nQ4eoDGL_2q7E):smirk: ( pylint 建議啟用 )，

當你安裝好 Importmagic 之後 ( 建議重啟 )，看下面這個例子，

當我輸入 `datetim` 的時候，他就會偵測到

![alt tag](https://i.imgur.com/PSTwXji.png)

必且有 auto import 的功能

![alt tag](https://i.imgur.com/eZKDzIE.png)

當你第二次再打的時候，可能輸入 `d` 就會跳出選項了。

![alt tag](https://i.imgur.com/LrqC6gz.png)

但今天假設是我們自訂的 Class 可以自動 import 嗎:question:

答案是不行的:cry:

![alt tag](https://i.imgur.com/7Fgn9Rl.png)

這時侯，我們就需要透過

[settings.json](https://github.com/twtrubiks/vscode_python_note/blob/master/.vscode/settings.json)

```json
{
    //"python.defaultInterpreterPath": "D:\\python_venv\\tutorial-venv\\Scripts\\python.exe",  //已說明過
    "python.linting.pylintEnabled": true, //已說明過
    "python.linting.enabled": true, //已說明過
    "python.autoComplete.extraPaths": [
        "D:\\python_venv\\tutorial-venv",  // 設定你的 venv 的環境目錄資料夾，為了偵測一些 python library
        "E:\\temp\\work\\self\\vscode_python_note\\src", // 目的是偵測自己自定義的 class
    ],
    "python.autoComplete.addBrackets": true, // 是否自動加上括號 (等等文章會補充說明)
    "files.autoSave": "afterDelay", // delay 後儲存
    "files.autoSaveDelay": 500,    // 延遲 500ms
}
```
這邊先補充說明一下 `"python.autoComplete.addBrackets": true`，

假設今天輸入 `import os`，然後輸入 `os.getcwd`，當他跳出提示給你選的時候，

當你選擇它，會自動幫你補括號，也就是 `os.getcwd()`; 相反的，如果是設定為

`false`，你就只會顯示 `os.getcwd`。 ( 如果這邊看不懂建議看影片說明 )

接著繼續講 [Importmagic](https://marketplace.visualstudio.com/items?itemName=brainfit.vscode-importmagic&fbclid=IwAR2WIhgRxvxeCv3vEGDc56dDQp2idFuDCDPgDqF2vXAiF7nQ4eoDGL_2q7E) 這個套件，

最重要的就是設定 `"python.autoComplete.extraPaths"`，

而且要設定正確，否則你會發現為什麼它不 work:question:

( 我這邊是指定某個資料夾底下的 Class 而已，如果你要讓它全部都偵測到，也可以設定

`"E:\\temp\\work\\self\\vscode_python_note"`，其實就是設定這個目錄 )

如果你設定正確，當你切換到任意 python 檔案的時候，

請注意下面 ( 很重要 :exclamation::exclamation::exclamation:我被雷到，想說怎麼沒 work )

![alt tag](https://i.imgur.com/2WRtyPi.png)

![alt tag](https://i.imgur.com/6ohigI0.png)

一定要讓他 scan 完以及 index 都跑完，這樣才會有效果，

當你每次改 code，儲存的時候也會重跑。

如果你設定正確，效果如下，可以偵測到自定義的 Class 了

![alt tag](https://i.imgur.com/4MS0RVx.png)

也有 auto import 的功能

![alt tag](https://i.imgur.com/b6C6aQ1.png)

第二次輸入，打幾個字就會跳出選項了

![alt tag](https://i.imgur.com/qx0XHHA.png)

以上就是 [Importmagic](https://marketplace.visualstudio.com/items?itemName=brainfit.vscode-importmagic&fbclid=IwAR2WIhgRxvxeCv3vEGDc56dDQp2idFuDCDPgDqF2vXAiF7nQ4eoDGL_2q7E) 的介紹。

## 結論

基本上 VSCode 可以設定的東西真的非常的多，大家可以自行摸索。:relaxed:

這篇是教大家一些很基本的設定，未來如果有機會，再介紹更多的功能給各位認識。

## Donation

文章都是我自己研究內化後原創，如果有幫助到您，也想鼓勵我的話，歡迎請我喝一杯咖啡:laughing:

![alt tag](https://i.imgur.com/LRct9xa.png)

[贊助者付款](https://payment.opay.tw/Broadcaster/Donate/9E47FDEF85ABE383A0F5FC6A218606F8)

## License

MIT license
