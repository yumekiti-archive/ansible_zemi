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
# git update-index --no-skip-worktree hosts
```

## rt-4331
```shell=
en
conf t

interface GigabitEthernet 0/0/0
    ip address dhcp
    no shut
exit

username admin password cisco

ip domain-name cisco.com

hostname R1

crypto key generate rsa
1024

ip ssh version 2

line vty 0 4
    login local
    transport input ssh
exit

enable secret cisco
```
