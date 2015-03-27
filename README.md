# omg-macbook

OMGで開発に必要なパッケージをインストールします

## 利用方法

### 1. Apple DeveloperサイトからCommand Line Toolをダウンロードしてインストールする
  * https://developer.apple.com/jp/

```
xcode-select --install
```

### 2. このリポジトリをForkして自分のインストールしたいソフトを `roles/homebrew/vars/main.yml` に追加する
  * https://github.com/Homebrew/homebrew/tree/master/Library/Formula
  * https://github.com/phinze/homebrew-cask/tree/master/Casks

### 3. aisibleのインストール

```
rake setup #=> install ansible your mac
```

### 4. パッケージのインストール

```
rake       #=> ansible playbook
```
