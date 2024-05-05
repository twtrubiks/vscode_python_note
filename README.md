# Python in Visual Studio Code

這篇文章將會教大家如何建立自己的 Visual Studio Code Python 開發環境 📝

* [Youtube - Visual Studio Code Python 基本設定篇](https://youtu.be/tS4beaq9ies)

* [推薦的擴充套件](https://github.com/twtrubiks/vscode_python_note/tree/master?tab=readme-ov-file#%E6%8E%A8%E8%96%A6%E7%9A%84%E6%93%B4%E5%85%85%E5%A5%97%E4%BB%B6)

## 說明

最近剛好接觸到使用 VSCode 開發 Python，所以就有了這篇文章:smile:

其實我之前都是使用 Pycharm Professional 來開發的 ( 雖然他要付費，但是功能真的強:+1:)

如果想當免費仔，可以使用 VSCode，但我覺得需要稍微設定一下 ( 這篇文章會教大家 )。

請先準備以下的功課

* 安裝 python 以及 Visual Studio Code

## 步驟一 - 建立 virtual environments

首先，別急著打開 VSCode，先來建立環境，如果你不知道如何建立環境，

可參考這篇文章

- [python venv 建立 virtual environments](https://github.com/twtrubiks/python-creation-of-virtual-environments)

- [使用 Anaconda 建立 Python 環境](https://github.com/twtrubiks/FaceDetect/tree/master/How%20Easy%20Install%20OpenCV%20%20for%20Python%20use%20Anaconda#%E4%BD%BF%E7%94%A8-anaconda-%E5%BB%BA%E7%AB%8B-python-%E7%92%B0%E5%A2%83)

- [pyenv 教學](https://github.com/twtrubiks/python-notes/tree/master/pyenv_tutorial)

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

可參考 [settings.json](https://github.com/twtrubiks/vscode_python_note/blob/master/.vscode/settings.json)

```json
{
    // User Settings

    // "python.defaultInterpreterPath": "/venv/bin/python3",
    // "window.zoomLevel": 1, // 視窗縮放
    "editor.fontSize": 22,
    "editor.lineHeight": 26,
    "terminal.integrated.fontFamily": "MesloLGS NF",
    "editor.fontFamily": "MesloLGS NF",
    "extensions.ignoreRecommendations": true, // 是否忽略顯示建議的套件
    "files.trimTrailingWhitespace": true, // 儲存的時候，會幫你自動過濾多餘的空格
    "files.encoding": "utf8", // 設定預設編碼
    "files.autoGuessEncoding": false,

    "files.autoSave": "onFocusChange", // 是否自動儲存檔案
    // "files.autoSave": "afterDelay",
    // "files.autoSaveDelay": 500,

    // "workbench.colorTheme": "One Dark Pro", // 需安裝 One Dark Pro
    "editor.selectionClipboard": false, // 關閉滑鼠滾輪中鍵複製功能
    "editor.stickyScroll.enabled": true, // Sticky Scroll 預設是打開的

    "[python]": {
        "editor.formatOnSave": true,
        "editor.codeActionsOnSave": {
            // "source.fixAll": "explicit",
            "source.organizeImports": "explicit",
          }
    },
    "editor.defaultFormatter": "charliermarsh.ruff" // 需要安裝 Ruff
    // "ruff.organizeImports": true
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

## 快捷鍵

環境以 linux 為主,

快速到對應找到對應的 function 或 class : `Ctrl` + 左鍵 或是 `F12`

返回上一個位置 : `Ctrl` + `Alt` + `-`

## 推薦的擴充套件

如何自動安裝, 已經幫大家放在 [extensions.json](https://github.com/twtrubiks/vscode_python_note/blob/master/.vscode/extensions.json),

```json
{
    "recommendations": [
        "streetsidesoftware.code-spell-checker",
        "donjayamanne.githistory",
        "ms-python.vscode-pylance",
        "ms-python.debugpy",
        "ms-python.python",
        "mechatroner.rainbow-csv",
        "charliermarsh.ruff",
        "gruntfuggly.todo-tree",
        "redhat.vscode-yaml",
        "zhuangtongfa.material-theme",
        "editorconfig.editorconfig"
    ]
}
```

打開 vscode 之後, 找到安裝 extensions 的地方, 輸入 `@recommended`,

就可以看到自己定義的 extensions,

![alt tag](https://i.imgur.com/y9s8M5v.png)

如果你想要建立自己的 extensions 清單,

可以直接在 extension 上點選右鍵

![alt tag](https://i.imgur.com/bVIWLG5.png)

就會自動幫你加入 [extensions.json](https://github.com/twtrubiks/vscode_python_note/blob/master/.vscode/extensions.json) 底下了.

官網說明可參考 [Workspace recommended extensions](https://code.visualstudio.com/docs/editor/extension-marketplace#_workspace-recommended-extensions)

### Todo Tree

顯示 TODO, FIXME, etc. comment tags in a tree view

[Todo Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)

### YAML

YAML 格式工具

[YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)

### Rainbow CSV

CSV 格式工具

[Rainbow CSV](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv)

### One Dark Pro

Atom's iconic One Dark theme

[One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)

### Git History

查看 git 的工具

[Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)

### Code Spell Checker

檢查錯字.

[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

### EditorConfig for VS Code

統一設定檔案 可參考 [.editorconfig](.editorconfig)

[EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

### Ruff

更強大更快的 Python linter (使用 Rust 寫的)

[Ruff](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff)

```cmd
pip install ruff
```

設定 Ruff 為預設的 formatter,

```json
{
  "[python]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "charliermarsh.ruff"
  }
}
```

設定自動 import 排版以及 fixAll

```json
{
  "[python]": {
    "editor.codeActionsOnSave": {
      "source.fixAll.ruff": "explicit",
      "source.organizeImports.ruff": "explicit"
    }
  }
}

```

### Python Debugger

[Python Debugger](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)

建議搭配 [Python debugging in VS Code](https://code.visualstudio.com/docs/python/debugging) 一起觀看

必要時需要安裝 `pip install debugpy`

`request` 主要有 `launch` 和 `attach`,

`launch`

這個就是最一般從 vscode 中 debug 重頭開始這樣.

`attach`

差別在於, 是調用已經啟動的進程, 意思就是必須再開一個視窗去執行這個 debug,

通常會用在已經運行的程式, 或是外部工具啟用的程序(像是 docker)

這兩個的差別使用 [vscode-django-note](https://github.com/twtrubiks/vscode_django_note) 來參考.

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Django launch",
            "type": "debugpy",
            "request": "launch",
            "program": "${workspaceFolder}\\manage.py",
            "args": [
                "runserver",
                "--noreload",
            ],
            "django": true
        },
        {
            "name": "Django attach",
            "type": "debugpy",
            "request": "attach",
            "connect": {
                "host": "localhost",
                "port": 18000
            },
            "django": true
        }
    ]
}
```

`launch` Django launch

這很簡單, 中斷點開下去就可以了.

`attach` Django attach

首先, 先打開一個 terminal 執行 django, 並且要監聽一個 port, 這邊設定 18000

```cmd
python -m debugpy --listen 0.0.0.0:18000 manage.py runserver 0.0.0.0:8000
```

接著再開啟一個 terminal 去執行中斷點 Django attach (也是設定 18000 port),

透過這個就可以成功的進入中斷點.

### Dev Containers

vsocde 可以在 docker 內建立容器並且開發.

[Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## 結論

基本上 VSCode 可以設定的東西真的非常的多，大家可以自行摸索。:relaxed:

這篇是教大家一些很基本的設定，未來如果有機會，再介紹更多的功能給各位認識。

## Donation

文章都是我自己研究內化後原創，如果有幫助到您，也想鼓勵我的話，歡迎請我喝一杯咖啡:laughing:

![alt tag](https://i.imgur.com/LRct9xa.png)

[贊助者付款](https://payment.opay.tw/Broadcaster/Donate/9E47FDEF85ABE383A0F5FC6A218606F8)

## License

MIT license
