# VSCode Remote Container Template

実際に使っているときのディレクトリ構造

```
|--.devcontainer
|  |--devcontainer.env
|  |--devcontainer.json
|  |--docker-compose.yml
|  |--alpine
|  |  |--Dockerfile
|  |--ssh
|  |  |--config
|  |  |--github
|  |  |--github.pub
|  |  |--known_hosts
|--.gitignore
|--README.md
```



## Githubへの接続
- `ssh-keygen`コマンドで作成
    - `./ssh/config`ではSSHキーが`github`と`github.pub`で作成することを前提にしている
    - 別名称にする場合は`./ssh/config`を修正してください
- 作成したkeyでの接続情報をknown_hostsに追加する

```
ssh-keyscan github.com >> ~/.ssh/known_hosts
```

## 環境変数
- `.devecontainer`の直下に`devcontainer.env`ファイルを配置すると読み込まれる
- `docker-compose.yml`で読み込む設定になっているため空ファイルで作成してください
    - もし作成したくない場合は`docker-compose.yml`から設定を外してください(13行目: `env_file: devcontainer.env`)
    - `devcontainer.env`はGithub上にあげないほうがよいこともあるので、デフォルトでは`.gitignore`の対象にしています

## default Extension(上から順)
- Vim
- Git Graph
- vscode-icons
- gitflow
- GitLens
- Indent-Rainbow
- Path Autocomplete
- Prettier
- REST Client
- TabNine Autocomplete
- GitHub Pull Requests and Issues
- Code Spell Checker

必要に応じて、追加削除をしてください。
`devcontainer.json`の`extension`を編集