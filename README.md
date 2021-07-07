#ManjaroKDE

- **_________________________________________**
 сохранить настройки дока и панели и виджеты
 mpv
- **_________________________________________**

- **Основные**
 1. **Обновить ядро**: `Manjaro Settings -> Ядра`

 2. **Обновить пакеты**: `sudo pacman -Syu`

 3. **Устройства ввода**:
    1. *Мышь*: `режим ускорения - плоский`; `Чувствительность: 5`
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

 7. **Перезагрузка**

 8. **Переприменить KDE Wallet**
 9. **Локализация** => Русский по стандарту
 10. **Установить сетевой драйвер**
 11. Pacman
    1. Enable AUR
    2. Russian mirror
 12. **Удалить мусор**
    `sudo pacman -Rs konversation`
 13. **Установка приложений**
    1. *Основное*: `sudo pacman -S gnome-keyring unzip bootsplash-systemd bootsplash-theme-manjaro latte ttf-droid youtube-dl mpv gimp neofetch simplescreenrecorder libreoffice-fresh libreoffice-fresh-ru telegram-desktop qbittorrent gparted nvm flameshot radeontop onlyoffice-desktopeditors dconf-editor aspell-ru ttf-fira-code etcher gimp-help-ru -y`
    2. *Опции*: `radeontool vulkan-radeon amdgpu-experimental amdvlk vulkan-headers`
    3. *Fonts*:
        1. `sudo pacman -S noto-fonts-cjk noto-fonts-emoji noto-fonts-extra ttf-cascadia-code ttf-droid ttf-fira-code ttf-fira-mono ttf-fira-sans ttf-inconsolata ttf-jetbrains-mono ttf-liberation ttf-meslo-nerd-font-powerlevel10k ttf-opensans ttf-roboto ttf-ubuntu-font-family gnu-free-fonts noto-fonts`
        2. `sudo pamac build ttf-mac-fonts ttf-meslo ttf-monaco ttf-ms-fonts ttf-windows adobe-base-14-fonts ttf-vista-fonts`
 14. **Install from AUR**
    `pamac build ttf-ms-fonts ttf-vista-fonts ttf-meslo spotify zoom adobe-base-14-fonts teams google-chrome mailspring gitkraken teamviewer jre minecraft-launcher visual-studio-code-bin`
 15. **Конфиги:**:
    1. Avito VPN: `unzip configs/Avito/vpn.zip -d ~/.avito`
    2. Gitconfig: `cp configs/.gitconfig ~/.gitconfig`
    3. ZSH: `cp config/ZSH/.zshrc ~/.zshrc && cp config/ZSH/.p10k.zsh ~/.p10k.zsh`

- **Compositor**
 1. Scale method: Smooth (slower)
 2. Rendering: XRender
 3. Latency: Balance
 4. Tearing: Automatic
 5. Keep window thumbnails: Only for Shown Windows

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
    4. Края экрана: `В левом верхнем углу - все приложения все раб. столы`

 - **Запуск и завершение**
    1. Вход в систему (SDDM): `WhiteSur`; `Nordic`
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

**Boot Splash**
 1. Установить: `bootsplash-systemd`; `bootsplash-theme-manjaro`
 2. **Редактировать**
    1. `/etc/mkinitcpio.conf` в `HOOKS` добавить `bootsplash-manjaro`
    2. `/etc/default/grub` в `DEFAULT` заменить `quiet` на `bootsplash.bootfile=bootsplash-themes/manjaro/bootsplash`
 3. `sudo mkinitcpio -P`
 4. `sudo update-grub`

**Включение меню выбора OS в GRUB**
 1. Редактировать настройки *GRUB*: `sudo nano /etc/default/grub`
 2. Установить: `GRUB_TIMEOUT_STYLE=menu`

**Включить AMDGPU для дескретной видеокарты**
 1. Редактировать настройки *GRUB*: `sudo nano /etc/default/grub`
 2. GRUB_CMDLINE_LINUX_DEFAULT >> `radeon.cik_support=0 amdgpu.cik_support=1 radeon.si_support=0 amdgpu.si_support=1`

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
 4. Копировать *.zshrc* и *p10k.zsh* в *~*

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
