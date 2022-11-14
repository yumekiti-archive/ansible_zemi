# 自動化について

# 背景
- インターンでCDN構築したけど1ミリも分からなかったので復習がてら自動化で構築してみる
- 複数の構築が面倒、人為的ミスが多い

# 目標
- CDN構成を自動構築する
- rt-4331にansibleで自動で設定できるようにする

# 内容

## 自動化とは
設定を自動的に実行する

## Ansible
レッドハットが開発するオープンソースの構成管理ツール

## やったこと
https://docs.ansible.com/ansible/2.9_ja/network/user_guide/network_best_practices_2.5.html
main.yml
```yaml!
- hosts: cisco
  gather_facts: no
  connection: local
  tasks:
    - name: send show version
      ios_config:
        commands: hostname R1
```

hosts
```shell!
[cisco:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_ssh_user=admin
cisco_enable_secret=cisco

ansible_connection=network_cli
ansible_network_os=ios

[cisco]
10.16.10.77
```

## エラーに遭遇
https://github.com/yumekiti/ansible_zemi/issues/1

## 懸念点
sshできるようにしておかないといけない
解決策としてコンソールサーバがあるがそんなものは無い

## 今後
とりあえず自動化ツールが実行されることが確認できたので簡易なネットワーク構成を組んで見る(VLANなど)

# まとめ
- やってること
    - 自動化
- やりたいこと
    - CDN構成の自動構築
- 今後
    - ネットワーク構築