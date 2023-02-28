# Шаги установки

1. Переходим в папку  ansible/ssh-keys и запускаем генерацию ssh-ключей (после генерации ключей нужно добавить ключ anisble.pub на [git-репозиторий Слёрм](https://gitlab.slurm.io/edu/xpaste_practicum)):
```sh
   cd ssh-keys
   ssh-keygen -f ansible
```
2. В корневой директории проекта запускаем инициализацию виртуальных машин:
```sh
   vagrant up
```
3. После инициализации виртуальных машин подключаемся к машине с установленным Ansible:
```sh
   vagrant ssh controlnode
```
4. На controlnode переходим в папку /home/vagrant/ansible, устанавливаем требуемые коллекции и роли и запускаем плейбук:
```sh
   ansible-galaxy install -r requirements.yml
   ansible-playbook playbook.yml
```
5. После успешного завершения работы плейбука открываем веб-браузер и переходим по ссылке:
```sh
http://192.168.0.202
```