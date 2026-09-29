# Домашнее задание: Ansible Roles (ClickHouse + Vector + Lighthouse)

## Ссылки на репозитории

- Vector role: https://github.com/kandroid83/vector-role
- Lighthouse role: https://github.com/kandroid83/lighthouse-role
- Playbook: https://github.com/kandroid83/ansible-playbook

## Что сделано

- Монолитный playbook разбит на отдельные роли vector-role и lighthouse-role.
- ClickHouse устанавливается через внешнюю роль AlexeySetevoi/ansible-clickhouse.
- Переменные разнесены между defaults/ и vars/ в каждой роли.
- Шаблоны конфигов (vector.toml, lighthouse.conf) вынесены в templates/.
- Настроены handlers для перезапуска vector и перезагрузки nginx.
- Теги v1.0.0 проставлены на обеих ролях по семантической нумерации.
- Итоговый playbook (site.yml) использует три роли через requirements.yml.

## Как запустить

    ansible-galaxy install -r requirements.yml -p roles/
    ansible-playbook -i inventory.ini site.yml

## Проверка

- ClickHouse слушает на http://localhost:8123
- Vector работает как systemd-сервис vector.service
- Lighthouse открывается на http://localhost
