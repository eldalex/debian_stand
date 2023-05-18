Плейбук для разворачивания и удаления тестового стенда debian 11 на KVM.
переменные:
create_stand.yml:
    pool_dir: каталог для диска ВМ
    download_url: адрес образа
    iso_name: имя образа
    iso_storage: каталог для хранения образов.
    checksum: хеш для проверки
    vm_net: дефолтная сеть
    ssh_pub_key: ваш публичный ключ, импортируется в машину на этапе подготовки
    vm_name: имя создаваемой машины
    default_root_pas: пароль root по умолчанию
    vm_ram_mb: объем памяти создаваемой ВМ
    vm_vcpus: количество CPU
    ipaddr: ip адрес

remove_stand.yml:
    pool_dir: каталог для диска ВМ
    vm_name: имя удаляемой машины
    ipaddr: ip адрес

Создание стенда:
ansible-playbook -K ./create_stand.yml
Создаст ВМ по указанным параметрам, закинет в неё ваш публичный ключ, добавит запись в etc/hosts и known_hosts текущего пользователя

Удаление стенда:
ansible-playbook -K ./remove_stand.yml
Удалит машину диск и все записи