# 第一個應用程式 Blog 系統
>要做一個讓使用者能夠發文的系統要有基本幾個功能：
>>可以新增使用者(User)  
>>使用者(User)可以對文章(Post)進行新增，修改，刪除

這裡我們先不用任何套件，僅靠 Rails 內建的功能(Scaffold)來完成它。

## 使用者功能
### Step1.使用 Scaffold
使用者會用到哪些資料

| 欄位名稱 | 資料型態 |
| ------- | ------- |
| name   |字串(String)|
|  email |字串(String)|
|  tel   |字串(String)|

 使用 Rails 內建的 Scaffold 功能來幫產生需要的檔案

**打這行指令的時候，記得要先用 cd 到 Rails 專案目錄裡**  

`$ rails generate scaffold User name:string email:string tel:string`
>如果覺得上面那行指令很長，可以濃縮成簡單的指令
>>1.generate 可以寫成 g
>>2.如果資料型態是 String 可以省略不寫，但**其他型態則不行**

**變成下面這行指令**  
`$ rails g scaffold User name email tel:`

### Step2.把描述具現化
db/migrate 目錄裡，有個可能長得像 20161220041724_create_users.rb 的檔案(前面的數字是時間，所以應該會跟各位的檔名不太一樣)，裡面的內容大概長這樣：
```ruby
class CreateUsers < ActiveRecord::Migration[5.0]
  def change
    create_table :users do |t|
      t.string :name
      t.string :email
      t.string :tel

      t.timestamps
    end
  end
end
```
從文字猜得出來它是要建立一個表格(table)，裡面有 name、email 以及 tel 三個欄位，分別都是字串(string)型態
現在要做的，就是執行這個遷移檔的描述，在資料庫建立一個名為 users 的表格，好讓我們把使用者的資料放進去

`$ rails db:migrate`

使用者的新增，刪除，更改功能現在已經完成了，所以只要啟動 Rails Sever 就好了

`$ rails server`

### Step4.開啟瀏覽器，連上 http://localhost:3000/users
#### 這樣使用者的功能就完成拉～

## 文章功能
接著是文章(Post)功能，大致上和使用者作法相同，但還會加上一些這兩個功能之間的關連性。

文章會到哪些資料

| 欄位名稱     | 資料型態    | 說明      |
| ----------- | ---------- | --------- |
| title      |字串(String) |文章標題   |
|  content   |文字(Text)   |內文      |
|  user_id   |數字(Integer)|使用者編號 |
|is_available|布林(Boolean)|文章是否上線|

**user_id 欄位的目的，是用來讓該編文章跟使用者連結在一起**

### Step1.使用 Scaffold
