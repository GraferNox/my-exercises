# my-exercises
для упражнения работы с Astra linux
после установки, как обычно, ненобходимо всё обновить:

sudo apt-get update && sudo apt-get upgrade

и включить удалённый доступ по ssh для root:

#устанавливаем openssh-server если не был установлен и ufw
apt install openssh-server ufw
#включаем службу ssh
systemctl enable sshd
#проверяем
ssh localhost
#копируем оригинальный конфиг и редактируем его
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.old
nano /etc/ssh/sshd_config
#по паролю параметр PermitRootLogin yes
#По ключу параметр PubkeyAuthentication yes
#рестартуем его
systemctl restart ssh
#добавляем правило
ufw allow 22

вот и всё, зная ip подключаемся к нашему серверу
чтобы узнать ip нашего хоста достаточно набрать команду

ip a
