# hidemaru_git_macros
秀丸エディタ用gitマクロ集

## 動作確認した環境
* git 2.19.1
  * `git.exe`へのパスが通っていること
* 秀丸エディタ 8.8.3
* WinMerge 日本語版 2.14.0+-jp-152

## gitlog.mac
* シンプルなログを表示する
* 修正点をつかみたいときに使う
* 実行結果は、アウトプット枠に出力する
```
git log ファイル名
```

## gitlogp.mac
* 詳細なログを表示する
* 実行結果は、アウトプット枠に出力する
```
git log -p ファイル名
```

## gitshowdiff.mac
* 指定のコミットと外部ツールを使った比較ができる
* git showで使うコミットハッシュがクリップボードにコピーされている状態で使うこと
* diffツールがインストールされていること
```
git show コミットハッシュ:ファイル名 > tempファイル名
diffツール ファイル名 tempファイル名
```

## gitblame.mac
* 各行のコミットハッシュと修正したアカウントを確認したいときに使う
* 選択した行の範囲でコミットハッシュと修正したアカウントを確認したいときに使う
  * 5行目から13行目までのコミットハッシュと修正したアカウントを確認する例
* 実行結果は、アウトプット枠に出力する
```
git blame ファイル名
git blame -L 5,13 ファイル名
```

## gitdiff.mac
* まだコミットが済んでいない差分を表示する
* 実行結果は、アウトプット枠に出力する
```
git diff -- ファイル名
```

## gitstatus.mac
* リポジトリの状況を表示する
* 実行結果は、アウトプット枠に出力する
```
git status
```

## github_search.mac
* カーソルのある単語でgithubを検索する
  * コミットハッシュでgithubを検索したいときなどに使う
