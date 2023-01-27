## Данный playbook выполняет следующие действия:

* Загружает дистрибутивы clickhouse и vector
* Устанавливает clickhouse
* Запускает clickhouse-server
* Создаёт базу 'logs' через clickhouse-client
* Устанавливает vector
* Запускает vector

## Для работы playbook необходимо:

* Предоставить доступы для работы ansible на хостах через ssh:
    * указать пользователя в файле `ansible_user`;
    * сгенерировать ssh ключи;
    * скопировать ssh ключи на хосты с помощью команды `ssh-copy-id`;
    * на хостах необходимо разрешить повышение роли без ввода пароля.
* Указать ip-адреса сервером в файле `inventory/prod.yml`.
* В файлах `vars.yml` указать необходимые версии дистрибутивов [clickhouse](https://packages.clickhouse.com/rpm/stable/) и [vector](https://packages.timber.io/vector/).
* Запустить playbook выполнив команду `ansible-playbook -i inventory/prod.yml site.yml`.