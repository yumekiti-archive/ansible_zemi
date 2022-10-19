# 2022後期ゼミ

```shell
ansible-galaxy init <name>
```

```shell
ansible-playbook -i hosts main.yml
```

## 疎通確認
```shell
ansible -i hosts cisco -m ping
```

## 変更を無視
```shell
git update-index --skip-worktree hosts
```