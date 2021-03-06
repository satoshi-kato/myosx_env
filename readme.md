# 環境構築

Macの環境を設定ファイルから構築していきます。  
巷ではAnsibleを更に組み合わせて自動化している人もいますが  
そこまでの手順ではないので、ここでは最低限の方法でやっています。  

## 登場人物
とりあえず、これさえ知っておけばなんとかなる  
* [Homebrew](http://qiita.com) - パッケージ管理ツール
* [HomebrewCask](https://caskroom.github.io) - Homebrewを使ってソフトウェアを一括インストールするための拡張機能
* [HomebrewBundle](https://github.com/Homebrew/homebrew-bundle) - Homebrewを使ってソフトウェアの依存関係をload／dumpできる拡張機能
* [mas](https://github.com/mas-cli/mas) - AppStoreのアプリを一括インストールするためのツール

## 構築してみる
このリポジトリにインストール一覧：[Brewfile](./Brewfile)があるので  
それをダウンロードして、HomebrewとHomebrewBundleのインストールからのロードでOKです。  
```bash:.sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew update
brew tap Homebrew/bundle
brew bundle
## インストール開始！！！
```

#### 上手くいかなくても
管理者権限があれば基本問題ないと思いますが、パーミッションでエラーになれば表示されるメッセージに従ってコマンドを実行すればなんとかなると思います。
```bash:.sh
sudo chown -R s-kato /usr/local/
```

## 設定の更新作業
HomebrewBundleで現状をすべて出力してBrewfileを生成してくれます。  
生成したBrewfileをこのリポジトリにpushすれば、同じ環境を構築可能です。  
```bash:.sh
brew bundle dump
```

## 最近の
homebrew-caskはデフォルトのインストール先が```~/Applications ```で、bash_profileとかでパスを変えていたが、  
今は通常のアプリディレクトリ```/Applications ```になったみたい　　

## その他
### npm
グローバルで使用するタスクランナーは入れておく  
```
npm install grunt -g
npm install gulp -g
```
### git
configとignoreファイルをコピー
### font 
http://www.rs.tus.ac.jp/yyusa/ricty_diminished.html
ダブルクリックでインストール
- RictyDiminishedDiscord-Bold.ttf
- RictyDiminishedDiscord-BoldOblique.ttf
- RictyDiminishedDiscord-Oblique.ttf
- RictyDiminishedDiscord-Regular.ttf
### vs code
英語化する
[F1] キー -> 「Configure Language」 -> 編集 -> 再起動
```
{
    // VSCode の表示言語を定義します。
    "locale":"en-US"
}
```
フォントを変更する
[F1] キー -> 「Open User Settings」 -> 追記 -> （保存で反映）
```
    "editor.fontFamily": "Ricty Diminished Discord",
    "editor.fontSize": 15,
    "editor.wrappingColumn": 130
```
### ssh
sshkeyを発行する
（パスフレーズも入れること）
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

### iterm2
themeを変更する
http://iterm2colorschemes.com/
- Earthsong
- Japanesque
- ManPage
- SolarizedDarkHigherContrast(def)
fontfamilyを変更する（上記でインストールしたやつ）
- RictyDiminishedDiscord-Regular
### システム環境設定
#### キーボード
ファンクションキーを有効にする
google日本語入力を登録する
### 設定ファイル
個人的に必要な設定ファイルもしれっと登録しています。  
これらを、```cp -a file ~/```すればいい感じになるはず。

## 参考

http://qiita.com/takustaqu/items/a328baf15862faa086ee