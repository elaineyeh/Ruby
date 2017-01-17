# Ruby

## 安裝開發環境
使用 arch 下這行指令
`sudo pacman -S ruby`

## 安裝 RVM
參考[官網](https://rvm.io/)兩行指令
```
一開始我們裝了 Ruby 在 /etc 下面 有些東西要刪，但是如果一開始沒裝 Ruby 就不用刪

    $ sudo rm -rf /etc/gemrc

接著，因為我們用的是 zsh 所以要改成 zshrc 所以要下一行指令

    $ echo "source~/.profile">>.zshrc

因為 rvm 會把他的設定寫到 ~/profile 中，所以我們把他的東西連到 (source) 我們 zsh 的設定檔中 (.zshrc)
```

## 使用 RVM
### 列出目前有哪些版本可以使用
`rvm list known `
### 下載2.4的版本
`rvm install 2.4 `

**RVM 會在每次開啟新的終端機視窗的時候回到預設值，所以如果希望每次開終端機視窗的時候都會自動切到 2.4 版的話**
`$ rvm 2.4 --default`

## 安裝 Rails
`gem install rails`
就完成拉～
