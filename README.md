# omg-macbook

Ansibleを利用してOMGで開発に必要なパッケージをインストールします

## 利用方法

### 1. Xcodeをダウンロードしてコマンドラインツールをインストールする

  * [Apple Developer Site](link-apple)

```
xcode-select --install
```

### 2. このリポジトリをForkする

![](https://raw.githubusercontent.com/mrtaddy/omg-macbook/master/images/fork_button.png)

### 3. インストールしたいソフトを追加する

  * 追加先
    * [roles/homebrew/vars/main.yml](link-main-yaml)

  * 参照先
    * [Formula](link-formula)
    * [Casks](link-casks)

### 4. aisibleのインストール

```
rake setup #=> install ansible your mac
```

### 5. パッケージのインストール

```
rake       #=> ansible playbook
```


## 標準でインストールされるパッケージ

### homebrew
- git
- imagemagick
- nodejs
- phantomjs
- rbenv
- ruby-build
- rbenv-default-gems
- readline
- openssl

### hombrew-cask
- flash
- github
- google-drive
- google-hangouts
- java
- mysql55-mavericks
- qt4-mac
- skype
- slack

### ruby
- CRuby 2.0.0-p643

### ruby gems
- bundler
- ec2ssh


## rake -T

```
$ rake -T
rake default            # ansible-playbook -i hosts -vv localhost.yml
rake playbook:homebrew  # ansible-playbook -i hosts -vv localhost.yml -t homebrew
rake playbook:rbenv     # ansible-playbook -i hosts -vv localhost.yml -t rbenv
rake setup              # setup ansible
```

[link-apple]:https://developer.apple.com/jp/
[link-formula]:https://github.com/Homebrew/homebrew/tree/master/Library/Formula
[link-casks]:https://github.com/phinze/homebrew-cask/tree/master/Casks
[link-main-yml]:https://github.com/mrtaddy/omg-macbook/blob/master/roles/homebrew/vars/main.yml
