## Данный playbook выполняет следующие действия:

* Загружает дистрибутивы clickhouse, vector и lighthouse
* Устанавливает clickhouse
* Запускает clickhouse-server
* Создаёт базу 'logs' через clickhouse-client
* Устанавливает vector
* Запускает vector
* Устанавливает lighthouse
* Устанавливает и запускает nginx для lighthouse

## Для работы playbook необходимо:

* Выполнить команды для создания переменных окружения:   
  ```shell
  export TF_VAR_yc_token=$(yc iam create-token)
  export TF_VAR_yc_cloud_id=$(yc config get cloud-id)
  export TF_VAR_yc_folder_id=$(yc config get folder-id)
  ```
* Запустить команду `terraform apply` для развертывания окружения в Yandex.Cloud
* Указать ip-адреса серверов в файле `inventory/prod.yml`.
* В файлах `vars.yml` указать необходимые версии дистрибутивов [clickhouse](https://packages.clickhouse.com/rpm/stable/) и [vector](https://packages.timber.io/vector/).
* Запустить playbook выполнив команду `ansible-playbook -i inventory/prod.yml site.yml`.