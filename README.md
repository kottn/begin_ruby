## begin_ruby
:beginner: はじめてのruby

#### Install rbenv
1. Clone rbenv into ~/.rbenv.
    ```
    $ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
    ```
1. `~/.profile`に追記
    ```bash
    export RBENV_ROOT="${HOME}/.rbenv"
    if [ -d "${RBENV_ROOT}" ]; then
        export PATH="${RBENV_ROOT}/bin:${PATH}"
        eval "$(rbenv init -)"
    fi
    ```

#### Install ruby-build
1. Rubyをインストールするためにはrbenvのプラグインruby-buildが必要
    ```
    $ mkdir -p ~/.rbenv/plugins
    $ cd ~/.rbenv/plugins
    $ git clone git://github.com/rbenv/ruby-build.git
    ```

#### Install ruby
  ```
  $ source ~/.profile
  $ rbenv install --list  # 確認
  $ rbenv install 2.5.0   # メモ時点の安定版
  ```
1. エラー吐かれた（Debian 9）
    ```
    BUILD FAILED (Debian 9.3 using ruby-build 20180224)
    .
    Inspect or clean up the working tree at /tmp/ruby-build.20180228164149.25348
    Results logged to /tmp/ruby-build.20180228164149.25348.log
    .
    .
    .
    ERROR: Ruby install aborted due to missing extensions
    Try running `apt-get install -y libssl-dev` to fetch missing dependencies.
    ```
1. 指示のとおりに`libssl-dev`をいれる
    ```
    $ sudo apt install libssl-dev
    ```
1. 再チャレンジ => :o:
    ```
    $ rbenv install 2.5.0
    Downloading ruby-2.5.0.tar.bz2...
    -> https://cache.ruby-lang.org/pub/ruby/2.5/ruby-2.5.0.tar.bz2
    Installing ruby-2.5.0...
    Installed ruby-2.5.0 to /home/kotani/.rbenv/versions/2.5.0
    ```
1. rubyやgemをインストールするたびに`rehash`しなきゃいけないらしい
    ```
    $ rbenv rehash
    ```
1. 切り替え
    ```
    $ rbenv versions
    $ rbenv global 2.5.0
    $ ruby --version
    ```
1. 毎回rehashはめんどいので自動でやってくれるやついれる
    ```
    $ git clone https://github.com/rbenv/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash
    ```
1. 端末再起動

#### gem install xxx
1. ためしに`tw`をインストールしてみる。
    ```
    $ gem install tw
    $ tw
    ```
できたみたい。
おわり。
