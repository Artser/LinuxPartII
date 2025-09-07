export BORG_PASSPHRASE='my_secure_backup_password_123'
export BORG_RSH='ssh -i /home/vagrant/.ssh/id_borg'

# Выполнять из client
## Посмотреть все архивы
borg list borg@192.168.1.100:/var/backup/borg-repo

## Посмотреть файлы в конкретном архиве
borg list borg@192.168.1.100:/var/backup/borg-repo::archive_name

# Просмотр логов
tail -f /var/log/borg-backup/backup-*.log

sudo journalctl -u borg-backup.service

# Выполнять из ansible
ssh-keygen
ssh-copy-id vagrant@192.168.1.100
ssh-copy-id vagrant@192.168.1.101
ansible-playbook -i inventory playbook.yml
