#ManjaroKDE

**Оформление**
 1. Оформление раб. среды: **Qokir Look-and-Feel Theme (Qogir-Dark)**
 2. Приложения: Breeze; GTK: Qogir-win-dark
 3. Раб. стол: Qogir-dark
 4. Оформление окон: Qogir-dark-circle-modified
    1. Границы: тонкие.
    2. Кнопки в заголовке: Поверх других окон; Заголовок; Скрыть; Раскрыть; Закрыть.
 5. Цвета:
    1. QogirManjaro
    2. QogirDark
    3. Qogir
 6. Шрифты:
    1. Hitting: полный.
    2. DPI: 96.
    3. Сглаживание: вкл.
 7. Значки:
    1. Tela manjaro
    2. Qogir manjaro (-dark)
 8. Курсор: Vimix
 9. Заставка Yaplass - Manjaro
 10. **Поведение рабочей среды**
    1. Блокировка экрана: 5 минут.
    2. После выхода из ждущего режима.
    3. **Внешний вид:** выбрать Manjaro обои.
 11. **Запуск и завершение**
    1. Вход в систему (SDDM): WhiteSur
        1. Выбрать Manjaro обои.

**Добавить Windows в GRUB**
 1. Вывести разделы: `lsblk`
 2. Найти EFI раздел и вывести информацию по нему: `sudo blkid /dev/sdX`
 3. Добавление своих записей в *GRUB*: `sudo nano /etc/grub.d/40_custom`
 4. Добавить в конец запись:
`--set=root - *(UUID из blkid, шаг 2)*
menuentry 'Windows 10' --class windows --class os {
    search --fs-uuid --no-floppy --set=root 1658-FDB0
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}`
 5. Обновить *GRUB*: `sudo update-grub`

**Включение меню выбора OS в GRUB**
 1. Редактировать настройки *GRUB*: `sudo nano /etc/default/grub`
 2. Установить: `GRUB_TIMEOUT_STYLE=menu`

**Включить AMDGPU для дескретной видеокарты**
 1. Редактировать настройки *GRUB*: `sudo nano /etc/default/grub`
 2. GRUB_CMDLINE_LINUX_DEFAULT >> `radeon.cik_support=0 amdgpu.cik_support=1 radeon.si_support=0 amdgpu.si_support=1"`

**Spotify fix**
 1. Вариант 1: `cd /usr/share/applications/ && sudo sed -i "s/"'Exec=spotify %U'"/"'Exec=spotify %U --no-zygote'"/" spotify.desktop && cd ~`
 2. Вариант 2: `cd /usr/share/applications/ && sudo sed -i "s/"'Exec=spotify %U'"/"'Exec=spotify %U --disable-gpu --disable-software-rasterizer'"/" spotify.desktop && cd ~`

**Установка NVM**
 1. Установка NVM: `sudo pacman -S nvm`
 2. Добавление NVM: `echo 'source /usr/share/nvm/init-nvm.sh' >> ~/.bashrc && exec $SHELL`
 3. Вывод всех доступных версий *NodeJS*: `nvm ls-remote`
 4. Установка *NodeJS*: `nvm install v(последняя LTS версия)`
 5. Выбора версии *NodeJS*: `nvm use ($lts)`

**ZSH**
 1. Выбрать ZSH активному пользователю: `chsh -s /usr/bin/zsh`
 2. Выбрать ZSH для SuperUser: `su -` и `chsh -s /usr/bin/zsh`
 3. Установить Oh-My-Zsh: `sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

**Настройка Chrome**
 1. `chrome://flags/`
 2. *Smooth Scrolling = Disabled*
 3. *Parallel Download = Enabled*

**Вывод инфорации по видеокарте**: `lspci -k | grep -EA3 'VGA|3D|Display'`

**Запуск TeamViewer службы**: `systemctl start teamviewerd.service`

**Открытый ключ Spotify**: `curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | gpg --import - Tip`
