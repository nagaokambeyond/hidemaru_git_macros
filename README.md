# hidemaru_git_macros
秀丸エディタ用gitマクロ集

## 動作確認した環境
* git 2.17.1
  * `git.exe`へのパスが通っていること
* 秀丸エディタ 8.8.3

## gitlog.mac
* シンプルなログを表示する
```
git log ファイル名
```

## gitlogp.mac
* 詳細なログを表示する
```
git log -p ファイル名
```

## gitdiff.mac
* まだコミットが済んでいない差分を表示する
```
git diff -- ファイル名
```

## github_search.mac
* カーソルのある単語でgithubを検索する
  * shaハッシュでgithubを検索したいときなどに使う
