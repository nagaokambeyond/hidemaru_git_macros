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
* gitに管理されているファイルであること
* 環境変数`TMP`に一時ファイルを作る→本マクロからは削除しない
* commit数に比例してgitからの応答が遅くなる
  * ブランチ用のマクロはブランチ全体であるため応答が遅い
  * git log --statは数秒待つことがあるため、条件を指定することを薦める

## 使い方🎉
### git_menu.mac
* 用意したマクロを呼び出すためのショートカットメニュー
* 詳しくは詳細を参照

# 詳細🎊
## ファイル用：アクティブなファイルに対して実行する
### git show+diff
* 指定のコミットと外部ツールを使った比較ができる
* 比較対象をメニューから選んで比較できる
  * 直近60commit
  * メニューに表示するcommitは左から70バイトで切っている
* 比較ツールがインストールされていること
* gitshowdiff.mac
```
git show コミットハッシュ:ファイル名 > tempファイル名
比較ツール ファイル名 tempファイル名
```

### git show
* 指定のコミットの内容を別の秀丸で表示する
 * 編集不可で表示する
* gitshow.mac
```
git show コミットハッシュ:ファイル名 > tempファイル名
hidemaru.exe tempファイル名 /p
```

### git blame
* 各行のコミットハッシュと修正したアカウントを確認したいときに使う
* 選択した行の範囲でコミットハッシュと修正したアカウントを確認したいときに使う
  * 5行目から13行目までのコミットハッシュと修正したアカウントを確認する例
* gitblame.mac
```
git blame ファイル名 > tempファイル名
git blame -L 5,13 ファイル名 > tempファイル名
hidemaru.exe tempファイル名 /p
```

### git log -p
* 詳細なログを表示する
* gitlog-p.mac
```
git.exe log -p --follow ファイル名
```

### git log format
* 書式をつけてログを表示する
* gitlog_format.mac
```
git.exe log --follow --date=iso --pretty=format:"[%ad] %h %an : %s" ファイル名 > tempファイル名
hidemaru.exe tempファイル名 /p
```

### git diff
* まだコミットが済んでいない差分を表示する
* 実行結果は、アウトプット枠に出力する
* gitdiff.mac
```
git diff -- ファイル名
```

### git log
* シンプルなログを表示する
* 修正点をつかみたいときに使う
* 実行結果は、アウトプット枠に出力する
* gitlog.mac
```
git log ファイル名
```

## ブランチ用：アクティブなブランチに対して実行する
### git log --stat
* 影響受けたファイルを表示する
* 条件を入力できる
* gitlog--stat.mac
```
git log --stat
```

### git log format all
* git log formatのブランチ全体用
* gitlog_format.mac
```
git.exe log --date=iso --pretty=format:"[%ad] %h %an : %s" > tempファイル名
hidemaru.exe tempファイル名 /p
```

### git branch -a
* ローカルとリモートのブランチを一覧表示する
* gitbranch-a.mac
```
git branch -a
```

### git status
* リポジトリの状況を表示する
* 実行結果は、アウトプット枠に出力する
* gitstatus.mac
```
git status
```

### github search
* githubを検索する
  * 未選択の場合、カーソル上の単語で検索
  * 選択中の場合、選択内容で検索
* github_search.mac
