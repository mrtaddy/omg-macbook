# omg-macbook

OMGで開発に必要なパッケージをインストールします

## 利用方法

#### 1. Xcodeをダウンロードしてコマンドラインツールをインストールする

  * https://developer.apple.com/jp/

```
xcode-select --install
```

#### 2. このリポジトリをForkする

![](https://raw.githubusercontent.com/mrtaddy/omg-macbook/master/images/fork_button.png)

#### 3. インストールしたいソフトを `roles/homebrew/vars/main.yml` に追加する

  * https://github.com/Homebrew/homebrew/tree/master/Library/Formula
  * https://github.com/phinze/homebrew-cask/tree/master/Casks

#### 4. aisibleのインストール

```
rake setup #=> install ansible your mac
```

#### 5. パッケージのインストール

```
rake       #=> ansible playbook
```

## 参考

```
$ rake -T
rake default            # ansible-playbook -i hosts -vv localhost.yml
rake playbook:homebrew  # ansible-playbook -i hosts -vv localhost.yml -t homebrew
rake playbook:rbenv     # ansible-playbook -i hosts -vv localhost.yml -t rbenv
rake setup              # setup ansible
```
