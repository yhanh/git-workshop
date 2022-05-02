# Node.js 4/30 上課筆記

## Git

### 終端機指令

- cd : change directory
- mkdir : 建立新的 file
- dir : 列出檔案列表

---

### git 的設定檔 `(設定檔是文字檔，可以直接編輯)`

- 全域： C:\Users\user\\.gitconfig

  - master 改成 main

        [init]
        defaultBranch = main

  - 快捷鍵設定

        [alias]
        co = checkout
        br = branch
        cm = commit
        st = status
        lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit --date=iso
        l = log --oneline --graph
        la = log --all --oneline --decorate --graph

- 區域： 在已經 init 過的檔案裡的隱藏資料夾 .git/config

  - master 改成 main

        git branch -m master main

---

### 新增、修改、刪除檔案

- 反悔加入暫存區，但保留檔案

        git rm --cached file

- 反悔加入暫存區，而且真的刪除檔案

        git rm -f file

- 比較檔案的差異 (確認後，可以按 q 離開)

        git diff

- 看 commitID 跟歷史紀錄

        git log

- 顯示修改檔案清單

        git status

- 已經加入過的檔案，可以不用 git add 再加一次，用 git commit -am "" 同時加入這次的修改與訊息

        git commit -am "訊息"

---

### Git Branch

- 檢視分支

        git branch

- 新增分支

        git branch {branch-name}

- 切換分支

        git switch {branch-name}

- 合併分支, 例如把 branch-b 合併進去 main

  - 先切換到 main

        git switch main

  - 再把 branch-b 合併進來

        git merge branch-b

- 分支的 push

  - 每個分支至少要做一次 -u 這樣之後可以直接 push

  - git push -u origin {branch} → -u 是 --set-upstream (設定上游)的縮寫

---

## Markdown

`通常會用 markdown 的語法來寫 README(副檔名 .md)`

### 標題

H1~H6 -> 標題前面 1 ~ 6 個 # 字號

E.g.

# H1 (# H1)

## H2 (# H2)

### H3 (# H3)

---

### 內文

- Bold : 粗體，使用兩個 +、- 符號

- Italic : 斜體 ，使用一個 +、- 符號

- Underline : 下劃線，使用 HTML \<u> 標籤

- Delete : 刪除線，使用兩個 ~ 符號

E.g.

Text **Bold** _Italic_ <u>underline</u> ~~delete~~

Text **Bold** _Italic_ <u>underline</u> ~~delete~~

---

### 清單

- Item : 項目符號使用 +、- 皆可

- Number : 數字項目使用 數字. 開頭，實際數字不影響渲染結果

- CheckBox : 任務清單，前方除 Item 符號以外，使用 [ ] 符號

  - [ ] : 渲染未打勾
  - [x] : 渲染為打勾

E.g.

- Item1
  - Item1.1
  - Item1.2

* Item2
  - Item2.1
  - Item2.2
    - Item2.2.1

1. Number
2. Number
3. Number

- [ ] CheckBox

* [x] To-Do

- [ ] To-Do

---

### 標註

- Highlight : 使用 `` 符號

E.g.

Text`Highlight`Remark

---

### 區塊

- Block : 文字前使用四個空格(跨佔整行)

E.g.

    Text Block

---

### 程式碼

- 區塊的語法類型，使用三個 ` 符號，後方加上程式語言名稱

- diff : 類似於 git 版本比對功能
  - \+ : 綠色代表新增
  - \- : 紅色代表刪除

E.g.

```JavaScript
// JavaScript
let a = "Hello Word"
console log(a);
```

```diff
+ System.out.println("Hello Word");
- System.out.println("Hello Word");
```

---

### 分隔線

- --- : 使用 \* 或 - 符號，數量要大於 三個

---

### 超連結

- Gitlab : 使用 <>符號，將網址渲染成超連結
- Blogger : 使用 [] 與 ()，將文字變成指定網址的超連結標籤
- YouTube : 另一種將文字變成指定網址的超連結方法，統一管理連結的網址

### Gitlab

<https://www.landscape-newstar.com/linlijyunhuangyunhan>

[Blogger](https://missyuan.cooking/blog-2/)

[Youtube]

[youtube]: https://www.youtube.com/watch?v=EgBJmlPo8Xw

---

### 表格

- Table - Align : 表格對齊方式，置左、置右、置中
- Table - Text : 表格中使用文字符號
- Table - Html : 在 Markdown 中，使用 Html 表格標籤
- Table - Span : 使用 Html 標籤，合併表格欄位
- Table - Mix : 混合使用 Markdown 格式與 Html 標籤
- Table - Item : 使用 Html 標籤，在表格中呈現項目列表

E.g.

### Table - Align

| Markdown            |               Simple |      Table      |
| :------------------ | -------------------: | :-------------: |
| left-aligned column | right-aligned column | centered column |
| $100                |                 $100 |      $100       |
| $10                 |                  $10 |       $10       |
| $1                  |                   $1 |       $1        |

### Table - Text

| 1        | 2            | 3        |
| -------- | ------------ | -------- |
| one      | two          | three    |
| _Italic_ | `Hightlight` | **Bold** |

### Table - Html

<table>
  <thead>
    <tr>
      <th>Month</th>
      <th>Savings</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>January</td>
      <td>$100</td>
    </tr>
    <tr>
      <td>February</td>
      <td>$80</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>Sum</td>
      <td>$180</td>
    </tr>
  </tfoot>
</table>

### Table - Span

<table>
  <tr>
    <th>Item1</th>
    <th>Item2</th>
    <th>Item3</th>
  </tr>
  <tr>
    <td>A1</td>
    <td colspan="2">A2</td>
  </tr>
  <tr>
    <td rowspan="2">B1</td>
    <td>B2</td>
    <td>B3</td>
  </tr>
  <tr>
    <td>C2</td>
    <td>C3</td>
  </tr>
</table>

---

### 參考

<https://www.youtube.com/watch?v=osPzqfqwmLA&ab_channel=GammaRay%E8%BB%9F%E9%AB%94%E5%B7%A5%E4%BD%9C%E5%AE%A4>

---

---

# Node.js 4/30 上課心得

第一天認識老師，第一印象覺得老師是個見識很廣而且非常有活力的老師。我在來資展學習之前不是相關科系畢業，也沒有學習過程式語言，在小專前第一次接觸到 JavaScript 的時候，處於一片混亂的狀態，到現在依然沒有很清楚 JavaScript 的運作邏輯。第一次上您的課的時候聽到之後會用很多的課堂來複習 JavaScript，便覺得有稍稍鬆了口氣的感覺，之後我會也會很認真地學，希望老師可以拯救我的 JavaScript！！
