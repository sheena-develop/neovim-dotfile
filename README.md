## WSL2(Ubuntu)で、最新のNeovimのインストール

aptでは、古いバージョンがインストールされてしまうため、以下の方法で最新版をインストールする

1. 古いNeovimの削除
```
sudo apt remove neovim
```

2. AppImageからNeovimをインストール
```
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim.appimage
```

3. 権限の変更
```
chmod u+x nvim.appimage
```

4. インストール
```
./nvim.appimage --appimage-extract
```

5. 最新バージョンがインストールされていることを確認
```
./squashfs-root/AppRun --version
```

6. 移動
```
sudo mv squashfs-root /
```

7. シンボリックリンクの設定
```
sudo ln -s /squashfs-root/AppRun /usr/bin/nvim
```

8. 確認
```
which nvim
```

9. 最新バージョンがインストールされていることを確認（[バージョン一覧](https://github.com/neovim/neovim/releases)）
```
nvim --version
```

## Amazon Linux 2023で、最新のNeovimのインストール

1. Neovimのダウンロード
```
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz
```

2. 削除
```
sudo rm -rf /opt/nvim
```

3. 解凍
```
sudo tar -C /opt -xzf nvim-linux64.tar.gz
```

4. .bashrc_profileに追加（~/.bashrc, ~/.zshrc, ...などでも可）
```
export PATH="$PATH:/opt/nvim-linux64/bin"
```

5. 最新バージョンがインストールされていることを確認（[バージョン一覧](https://github.com/neovim/neovim/releases)）
```
nvim --version
```

## フォント設定

Neovimでアイコンなどを表示するため、Nerdフォントのインストールを推奨します

- **フォントのダウンロード**：[0xProto GitHubページ](https://github.com/0xType/0xProto)

## Windows Terminalの設定

Windows Terminalで使用するフォントや透明度をカスタマイズするには、`settings.json`を編集します

```
{
  "profiles": {
    "defaults": {
      "font": {
        "face": "0xProto Nerd Font"
      },
      "opacity": 85,
      "useAcrylic": false
    },
    "list": [
      ...
    ]
  }
}
```

## リポジトリのクローン

Neovimの設定リポジトリをクローンするためのコマンド:</br>
`git clone [Repository URL] ~/.config`

**注意**：`~/.config`ディレクトリが既に存在し、他の設定が保存されている場合、このコマンドは上書きのリスクがあるため注意してください
## インストール手順
1. Neovimの最新バージョンがインストール済みであること
2. node.jsがインストール済みであること
3. フォント（0xProto）がインストール済みであること
4. `sudo apt update`
5. `sudo apt install -y python3 python3-pip`
6. `pip3 install -U pynvim 'python-lsp-server[all]' pylsp-mypy python-lsp-isort python-lsp-black
`
7. `npm install -g pyright`
8. `npm install -g vim-language-server`

## ディレクトリ構成と各ディレクトリの役割
- after/ftplugin/：ファイルタイプごとの追加設定
- autoload/：自動読み込みされる関数やスクリプト
- docs/：設定に関するドキュメントやガイド
- ftdetect/：ファイルタイプの検出に関する設定
- lua/：Luaで記述された設定ファイルやプラグインの設定
- my_snippets/：ユーザー定義のスニペット
- plugin/：プラグインの設定や初期化スクリプト
- resources/：設定に関連するリソースファイル（例: 画像やテンプレート）
- spell/：スペルチェック用の辞書ファイル
- viml_conf/：VimLで記述された追加の設定ファイル
- .stylua.toml：Luaの設定ファイル
- _config.yml：
- ginit.vim：GUI版Neovim（例: nvim-qt）用の追加設定
- init.lua：Neovimのメインの設定ファイルで、全体のエントリーポイント


## ショートカット

ここに頻繁に使用するショートカットの一覧を示します。以下のショートカットで、`<leader>` は ASCII 文字 `,` を表します。

| ショートカット        | モード       | プラットフォーム | 説明                                                                  |
|-----------------------|--------------|------------------|-----------------------------------------------------------------------|
| `<leader>ff`         | ノーマル     | Linux/macOS/Win | 浮動ウィンドウでファイルをあいまい検索                               |
| `<leader>fh`         | ノーマル     | Linux/macOS/Win | 浮動ウィンドウでヘルプファイルをあいまい検索                         |
| `<leader>fg`         | ノーマル     | Linux/macOS/Win | 浮動ウィンドウでプロジェクト全体をあいまい検索                       |
| `<leader>ft`         | ノーマル     | Linux/macOS/Win | 浮動ウィンドウでバッファタグをあいまい検索                           |
| `<leader>fb`         | ノーマル     | Linux/macOS/Win | 浮動ウィンドウでバッファを切り替え                                   |
| `<leader><Space>`    | ノーマル     | Linux/macOS/Win | 行末の空白を削除                                                     |
| `<leader>v`          | ノーマル     | Linux/macOS/Win | 最後に貼り付けたテキストを再選択                                     |
| `<leader>ev`         | ノーマル     | Linux/macOS/Win | 新しいタブで Neovim の設定を編集                                     |
| `<leader>sv`         | ノーマル     | Linux/macOS/Win | Neovim の設定をリロード                                              |
| `<leader>st`         | ノーマル     | Linux/macOS/Win | カーソル位置のテキストのハイライトグループを表示                     |
| `<leader>q`          | ノーマル     | Linux/macOS/Win | 現在のウィンドウを閉じる                                             |
| `<leader>Q`          | ノーマル     | Linux/macOS/Win | すべてのウィンドウを閉じ、Neovim を終了                              |
| `<leader>w`          | ノーマル     | Linux/macOS/Win | 現在のバッファ内容を保存                                             |
| `<leader>y`          | ノーマル     | Linux/macOS/Win | バッファ全体の内容をデフォルトレジスタにコピー                       |
| `<leader>cl`         | ノーマル     | Linux/macOS/Win | カーソルの列をトグル                                                 |
| `<leader>cd`         | ノーマル     | Linux/macOS/Win | 現在のバッファのディレクトリに作業ディレクトリを変更                 |
| `<space>t`           | ノーマル     | Linux/macOS/Win | タグウィンドウのトグル（右ウィンドウでプロジェクトタグを表示）       |
| `<leader>gs`         | ノーマル     | Linux/macOS/Win | Git のステータスを表示                                               |
| `<leader>gw`         | ノーマル     | Linux/macOS/Win | 現在のファイルを Git add                                             |
| `<leader>gc`         | ノーマル     | Linux/macOS/Win | git commit を実行                                                    |
| `<leader>gpl`        | ノーマル     | Linux/macOS/Win | git pull を実行                                                      |
| `<leader>gpu`        | ノーマル     | Linux/macOS/Win | git push を実行                                                      |
| `<leader>gbd`        | ノーマル     | Linux/macOS/Win | ブランチを削除                                                       |
| `<leader>gbn`        | ノーマル     | Linux/macOS/Win | 新しいブランチを作成                                                 |
| `<leader>gl`         | ノーマル/ビジュアル | Linux/macOS/Win | 現在または選択行のパーマリンクを取得                              |
| `<leader>gbr`        | ノーマル     | macOS           | 現在の Git リポジトリをブラウザで表示                                |
| `<leader>gb`         | ビジュアル   | macOS           | 現在の行の責任者を表示                                               |
| `<F9>`               | ノーマル     | Linux/macOS/Win | 現在のソースファイルをコンパイル＆実行（C++, LaTeX, Lua, Python）    |
| `<F11>`              | ノーマル     | Linux/macOS/Win | スペルチェックのトグル                                               |
| `<F12>`              | ノーマル     | Linux/macOS/Win | ペーストモードのトグル                                               |
| `\x`                 | ノーマル     | Linux/macOS/Win | ロケーションまたはクイックフィックスウィンドウを閉じる               |
| `\d`                 | ノーマル     | Linux/macOS/Win | 現在のバッファを閉じ、前のバッファに戻る                             |
| `{count}gb`          | ノーマル     | Linux/macOS/Win | `{count}` 番目または次のバッファに移動                              |
| `{operator}iB`       | ノーマル     | Linux/macOS/Win | 全バッファでの操作（`{operator}` は `v`, `y`, `c`, `d` など）       |
| `Alt-k`              | ノーマル     | Linux/macOS/Win | 現在の行または選択行を上に移動                                       |
| `Alt-j`              | ノーマル     | Linux/macOS/Win | 現在の行または選択行を下に移動                                       |
| `Alt-m`              | ノーマル     | macOS/Win       | システムブラウザで Markdown プレビューを表示                         |
| `Alt-Shift-m`        | ノーマル     | macOS/Win       | システムブラウザでの Markdown プレビューを停止                       |
| `ob`                 | ノーマル/ビジュアル | macOS/Win | カーソル下のリンクを開く、または選択内容で検索                    |
| `ctrl-u`             | 挿入        | Linux/macOS/Win | カーソル下の単語を大文字に変換                                       |
| `ctrl-t`             | 挿入        | Linux/macOS/Win | カーソル下の単語をタイトルケースに変換                               |
| `jk`                 | 挿入        | Linux/macOS/Win | ラグなしでノーマルモードに戻る                                       |

## カスタムコマンド

いくつかのプラグインによるコマンドに加えて、個人用にカスタムコマンドも作成されています。

| コマンド       | 説明                                                                       | 例                             |
|----------------|----------------------------------------------------------------------------|--------------------------------|
| `Redir`        | コマンドの出力をタブページにキャプチャし、簡単に確認                       | `Redir hi`                     |
| `Edit`         | 複数のファイルを同時に編集（グロブ対応）                                   | `Edit *.vim`                   |
| `Datetime`     | 現在の日付と時刻を表示、または Unix タイムスタンプを日付に変換            | `Datetime 12345` または `Datetime` |
| `JSONFormat`   | JSON ファイルを整形                                                       | `JSONFormat`                   |　
