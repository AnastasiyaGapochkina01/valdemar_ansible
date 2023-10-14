[Синтаксис Yaml](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)

1) Поднять две виртуалки: одна master, с которой будем катать плейбуки; вторая - node, куда будем катить
2) Настроить доступность между виртуалками через пользователя ansible (ssh по ключам)
3) Установить на мастер ansible
4) Создать директорию, где будут хранится роли и плейбуки, создать там файл inventory, в котором прописать адрес node
5) Проверить свзяность
ansible -i $inventory all -m ping
В ответе должно быть
"ping": "pong"
6) Запустить команду ansible -i $inventory all -m ping с ключом -v (-vvv), для расширенного вывода
7) Написать плейбук, который будет пинговать node и выводить ответ на ping, Запустить ([пример](https://github.com/AnastasiyaGapochkina01/valdemar_ansible/blob/main/ansible/ping_playbook.yaml))
8) Написать роль, которая поставит на node nginx, удалит файл default (/etc/nginx/sites-*), сделает после этого проверку конфигурации и релоад (использовать механизм handlers) [Пример роли](https://github.com/AnastasiyaGapochkina01/valdemar_ansible/tree/main/ansible/roles/setup_nginx)
9) Скопировать роли [setup_postgres](https://github.com/AnastasiyaGapochkina01/valdemar_ansible/tree/main/ansible/roles/setup_postgres) и [setup_python3.10](https://github.com/AnastasiyaGapochkina01/valdemar_ansible/tree/main/ansible/roles/setup_python3.10) в папку roles и написать плейбук, который прокатает по node три роли
    - setup_postgres
    - setup_nginx
    - setup_python3.10
