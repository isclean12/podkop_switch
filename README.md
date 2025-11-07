[README.txt](https://github.com/user-attachments/files/23421493/README.txt)
# Скрипт управления Podkop с сохранением интернета
# Автор: isclean
# Версия: 1.0

# Что делает скрипт при выключении:
# ✅ Сохраняет резервную копию DNS

# ✅ Устанавливает рабочие DNS серверы

# ✅ Корректно останавливает службы

# ✅ Отключает автозагрузку

# ✅ Восстанавливает работу DNSMASQ

# ✅ Проверяет результат

# Шаг 1: Создайте файл скрипта
nano /usr/bin/podkop-switch

# Шаг 2: Добавьте содержимое скрипта из файла

# Шаг 3: Сделайте скрипт исполняемым
chmod +x /usr/bin/podkop-switch

# Показать доступные комманды
podkop-switch help

# Быстрые команды
# Включить Podkop
podkop-switch on

# Выключить Podkop (с сохранением интернета)
podkop-switch off

# Статус всех служб
podkop-switch status

# Только проверка DNS
podkop-switch dns

# Дополнительные улучшения
# Создайте псевдонимы для удобства:
# Откройте файл профиля
nano /etc/profile

# Добавьте в конец файла:
alias pon='podkop-switch on' 
alias poff='podkop-switch off' 
alias pstatus='podkop-switch status' 
alias pdns='podkop-switch dns' 

# Перезагрузите профиль
source /etc/profile

# Или просто перезайдите в SSH
exit
# и снова подключитесь
ssh root@192.168.1.1

# Посмотрите все активные псевдонимы
alias

# Должны увидеть:
# pon='podkop-switch on'
# poff='podkop-switch off'
# pstatus='podkop-switch status'
# pdns='podkop-switch dns'

# Тестируем команды:
pon      # Включить Podkop
pstatus  # Проверить статус
poff     # Выключить Podkop

# Полный список полезных псевдонимов:
# Основные команды Podkop
alias pon='podkop-switch on' 
alias poff='podkop-switch off' 
alias pstatus='podkop-switch status' 
alias pdns='podkop-switch dns' 

# Дополнительные команды
alias plog='logread | grep podkop' 
alias psinglog='logread | grep sing-box' 
alias pconfig='show_sing_box_config' 
alias pnft='nft list table inet PodkopTable' 

# Удаление псевдонимов:
# Удалить конкретный псевдоним
unalias pon

# Удалить все псевдонимы
unalias -a
