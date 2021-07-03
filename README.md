#ManjaroKDE

- **_________________________________________**
 1. Бинды клавиш
 2. Дописать программы
 3. Сохранить конфиги (ВПН, гит, баш, зш)
 4. Сохранить обои
- **_________________________________________**

- **Основные**
 1. **Обновить ядро**: `Manjaro Settings -> Ядра`
 2. **Обновить пакеты**: `sudo pacman -Syu`
 3. **Устройства ввода**:
    1. *Мышь*: `режим ускорения - плоский`
    2. *Сенсорная панель*: `Естественная прокрутка` и `Эмуляция кнопок мыши`
 4. **Управление питанием**:
    1. Приостановка сеанса: `В ждущий режим - 15 мин.`
    2. При закрытии крышки ноутбука: `Ничего не делать`
 5. **Экран**:
    - *Обеспечение эффектов*
    1. Включить граф. эффекты при входе в систему
    2. **Метод машстабирования**: `Со сглаживанием`
    3. **Механизм отрисовки**: `XRender`
    4. **Задержка отрисовки**: `Предпочитать низкую задержку`
    - *Ночная цветовая схема*
    1. Использовать ночную цветовую схему: `3300K`; `От заказа до рассвета`
 6. **Поиск**
    - *Поиск файлов*
    1. Отключить индексирование содержимого файлов
    - *Строка поиска*
    1. В центре
    2. Модули: `KWin`; `Завершение приложений`; `Запуск программ`; `Калькулятор`; `Окна`; `Преобразование величин`; `Расположения`; `Точки входа`
 7. **Локаклизация**:
    1. *Язык*: `Русский (По умолчанию)`
 8. **Диспетчер окон**:
    - *Поведение окон*
    1. Дополнительно: `По центру`; `Не разрешать сохранять геометрию`
    - *Переключение окон*: `Показывать выбранное окно`; `Сетка миниатюр`


7. **Reboot**

8. **Reapply KDE Wallet**
9. Localization => Russian as default
10. Install network driver
11. Pacman
    1. Enable AUR
    2. Russian mirror
12. **Remove trash**
    `sudo pacman -Rs konversation`
13. **Install applications**
    `sudo pacman -S gnome-keyring gimp neofetch simplescreenrecorder libreoffice-fresh libreoffice-fresh-ru telegram-desktop dconf-editor aspell-ru ttf-fira-code etcher gimp-help-ru -y`
14. **Install from AUR**
    `pamac build ttf-ms-fonts ttf-vista-fonts spotify zoom teams google-chrome mailspring gitkraken teamviewer jre minecraft-launcher visual-studio-code-bin`

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


 - **Поведение рабочей среды**
    1. Блокировка экрана: 5 минут.
    2. После выхода из ждущего режима.
    3. **Внешний вид:** выбрать Manjaro обои.

 - **Запуск и завершение**
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

**Oh my Bash и Agnoster theme**
 1. `bash -c "$(wget https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh -O -)"`
 2. `sed -i "s/"font"/"agnoster"/" .bashrc`

**Настройка Chrome**
 1. Перейти в настройки *Chrome*: `chrome://flags/`
 2. *Smooth Scrolling = Disabled*
 3. *Parallel Download = Enabled*

**Swappiness 10%**:
 1. `sudo nano /etc/sysctl.d/100-manjaro.conf` >> `vm.swappiness=10`
 2. `sudo sysctl vm.swappiness=10`

**Запуск SSDTrim**: `sudo systemctl start fstrim.timer`

**Запуск программ с DRI_PRIME=1**: `su -c'echo DRI_PRIME=1 >>  /etc/environment'`

**KDE виджеты**: `mediacontroller_plus`; `application menu`; `latte spacer`; `better inline clock`

**Вывод инфорации по видеокарте**: `lspci -k | grep -EA3 'VGA|3D|Display'`

**Запуск TeamViewer службы**: `systemctl start teamviewerd.service`

**Открытый ключ Spotify**: `curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | gpg --import - Tip`
