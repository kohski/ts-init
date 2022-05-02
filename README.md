# githubのrepoを作る
```bash
# ghqでlocal repositoryを作成する
# fzf + ghqの環境を整備しておくと便利(参考: https://qiita.com/tomoyamachi/items/e51d2906a5bb24cf1684)
$ ghq create <user>/<reponame>

# ディレクトリを移動する
$ cd ~/repos/github.com/<user>/<reponame> 

# remoteリポジトリを作る => promptには適宜回答する
$ gh repo create

# 最低限の.gitignoreを追加
$ echo -e "**/node_modules\n**/dist" > .gitignore
```

# TypeScriptのセットアップ
```bash
# yarnを用いてプロジェクトを作成。ひとまずは全部デフォルトで実施。
$ yarn init -y

# 最低限のパッケージを追加
$ yarn add --dev typescript @types/node

# tsconfig.jsonの雛形を作成
$ tsc --init
```

# tsconfig.jsonを編集
以下の設定をします。(ブルーベリー本第9章を参考にしています)
- targetを`es2020`にする
- compilerOptions.outDirを`./dist`に変更
- includeを`./src`に変更
- exactOptionalPropertyTypesを追加
- noUncheckedIndexedAccessを追加

```json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "commonjs",
    "outDir": "./dist",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "exactOptionalPropertyTypes": true,
    "noUncheckedIndexedAccess": true,
    "skipLibCheck": true
  },
  "include": ["./src/**/*.ts"]
}
```
