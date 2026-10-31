[English](README.md) | 日本語

# Global Configurations

このリポジトリは、複数のプロジェクトとユーザーの開発環境で共通利用する開発・CI設定の管理元です。Git submodule として取り込み、各プロジェクトやユーザー共通設定から同じ設定ファイルを参照することを想定しています。

## 収録している設定

現在、次の設定を収録しています。

- EditorConfig と Git ignore
- Markdownlint、textlint（辞書・allowlist を含む）
- Commitlint
- GitHub Actions のワークフローとセキュリティチェック
- GitHub Actions の lint・シークレットスキャン用設定

最新の収録内容はリポジトリ内のファイルを確認してください。

## submodule として追加する

利用する側のリポジトリで、構成に合ったパスを指定して追加します。

```sh
git submodule add https://github.com/aglabo/global-configs.git path/to/global-configs
git submodule update --init --recursive
```

プロジェクトでは、プロジェクト内の設定用ディレクトリに配置できます。ユーザー共通設定では、ホームディレクトリの設定を管理する Git リポジトリに `.config/global-configs` のようなパスで追加します。

submodule を追加すると設定ファイルを参照できるようになりますが、ツールや GitHub Actions が自動でその設定を読み込むわけではありません。各ツール、runner、workflow に、submodule 内の設定ファイルを読むよう指定してください。利用側のリポジトリで実行する GitHub Actions workflow は、そのリポジトリの `.github/workflows` から実行されるように接続する必要があります。

## 更新する

リモートの最新状態を取得し、利用側のリポジトリに記録します。

```sh
git submodule update --remote path/to/global-configs
git add path/to/global-configs
git commit -m "chore: update global configs"
```

コミット前に差分を確認し、利用側で採用する設定の版を記録してください。

## ライセンス

このリポジトリは MIT License で提供されています。詳細は [LICENSE](./LICENSE) を参照してください。
