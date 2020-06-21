# Задания
- Create a role that configures an Apache vhost on the managed hosts in the group "lamp"
- Have it include a template to create a minimal vhost configuration file in which all references to the hostname are replaced with Ansible facts
- Use an ad-hoc commands to test working of the vhost

# Решение
 
файл playbook: hw-3/configure_httpd.yml  
каталог роли: hw-3/roles/configure_httpd  
Алгоритм:
- Установка пакета httpd (если пакет отсутствует)
- Создание корневого каталога для vhost
- Копирование шаблона для vhost на управляемую ноду и вызов handler для перезапуска httpd  
В шаблоне используются данные из ansible_facts для указания server_name и корневого каталога vhost
- Открытие используемых портов
