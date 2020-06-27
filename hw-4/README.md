# Задания
- Исправить [проект](https://bitbucket.org/astrukov/hw_fixme/src/master/) так, чтобы playbook отработал без ошибок

# Решение
 
## hw-playbook.yml:  
- скопировал `vars` и `tasks` из hw-copy-facts.yml
- task "create index.html"
  - добавил опцию force, т.к. шаблон может меняться со временем. Без force шаблон будет применен только в самый первый раз - при создании файла из шаблона.
- task "open the port for the smb service"
  - `service: smb` => `service: samba`
    
## hw-copy-facts.yml:
- удалил, т.к. это вообще не playbook файл

## custom.fact:
- packages.smb_package
  - `smb` => `samba`
- packages.ftp_package 
  - `vsfptd` => `vsftpd`
- packages.web_package 
  - проблема с кодировкой в слове httpd
- services.ftp_package: 
  - `vsfptd` => `vsftpd`
- services.web_package
  - проблема с кодировкой в слове httpd

## hw-tasks/lamp.yml:
 - task "install and start the servers" 
   - добавил `ansible_local.custom.packages.db_package`
 - task "start database server" 
   - `ansible_local.custom.services.ftp_service => ansible_local.custom.services.db_service`

    