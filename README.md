# hidemaru_git_macros🌈
秀丸エディタ用gitマクロ集

## 動作確認した環境💻
* git 2.19.1
  * `git.exe`へのパスが通っていること
* 秀丸エディタ 8.8.3
* WinMerge 日本語版 2.14.0+-jp-152

## インストール方法🔧
* コマンドラインからローカルにクローンする
* 秀丸で(M)マクロ-(E)マクロ登録を開く
* マクロ登録で`git_menu.mac`を登録する

## 注意⚠
* アクティブなファイルに対して実行する
  * gitに管理されているファイルであること
* 環境変数`TMP`に一時ファイルを作る

## 使い方🎉
### git_menu.mac
* 用意したマクロを呼び出すためのショートカットメニュー
* 詳しくは詳細を参照

## 詳細🎊
### gitshowdiff.mac
* 指定のコミットと外部ツールを使った比較ができる
* 比較対象をメニューから選んで比較できる
  * 直近60commit
  * メニューに表示するcommitは左から70バイトで切っている
* 比較ツールがインストールされていること
```
git show コミットハッシュ:ファイル名 > tempファイル名
比較ツール ファイル名 tempファイル名
```

### gitshow.mac
* 指定のコミットの内容を別の秀丸で表示する
 * 編集不可で表示する
```
git show コミットハッシュ:ファイル名 > tempファイル名
hidemaru.exe tempファイル名 /p
```

### gitblame.mac
* 各行のコミットハッシュと修正したアカウントを確認したいときに使う
* 選択した行の範囲でコミットハッシュと修正したアカウントを確認したいときに使う
  * 5行目から13行目までのコミットハッシュと修正したアカウントを確認する例
```
git blame ファイル名 > tempファイル名
git blame -L 5,13 ファイル名 > tempファイル名
hidemaru.exe tempファイル名 /p
```

### gitlog-p.mac
* 詳細なログを表示する
```
git log -p ファイル名
```

### gitlog_format.mac
* 書式をつけてログを表示する
  * git_menu.macから`git log format all`で起動した場合、現在のブランチ全体を対象にする
```
git.exe log --date=iso --pretty=format:"[%ad] %H %an : %s ファイル名 > tempファイル名
git.exe log --date=iso --pretty=format:"[%ad] %H %an : %s > tempファイル名
hidemaru.exe tempファイル名 /p
```

### gitdiff.mac
* まだコミットが済んでいない差分を表示する
* 実行結果は、アウトプット枠に出力する
```
git diff -- ファイル名
```

### gitlog.mac
* シンプルなログを表示する
* 修正点をつかみたいときに使う
* 実行結果は、アウトプット枠に出力する
```
git log ファイル名
```

### gitlog-stat.mac
* 影響受けたファイルを表示する
* 条件を入力できる
```
git log --stat
```

### gitbranch-a.mac
* ローカルとリモートのブランチを一覧表示する
```
git branch -a
```

### gitstatus.mac
* リポジトリの状況を表示する
* 実行結果は、アウトプット枠に出力する
```
git status
```

### github_search.mac
* githubを検索する
  * 未選択の場合、カーソル上の単語で検索
  * 選択中の場合、選択内容で検索
