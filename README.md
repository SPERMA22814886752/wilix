молодежный дистр wilix с ядром 4.19
----------
сборка:

скачайте ядро линукс 4.19 и соберите его с конфигом который приложен в проекте, потом скопируйте скрипты и запустите их, вот примерные команды:

```bash
sudo apt install libncurses-dev  # семейство дебиан и убунту
sudo xbps-install ncurses-devel  # void
sudo pacman -S ncurses           # семейство арч
wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.19.325.tar.xz # скачивание ядра
tar -xf linux-4.19.325.tar.xz # распаковка
cd ~/linux-4.19.325
rm .config # удаляем старый конфиг
cp ~/wilix/.config .
make menuconfig # если надо подредактировать самому
make -j$(nproc) bzImage
file arch/x86/boot/bzImage # собралось?
cd ~/wilix
chmod +x start && chmod +x grub # для исполнения
./start
./grub
qemu-system-x86_64 -cdrom wilixos.iso # запуск
```

------------
устанавливание приложений:

к сожалению я пока не сделал пакетный мененджер но можете качать библеотеки и приложения вручную, есть тестовая версия браузера но не факт что работает

------------
инфо:

библеотека musl, архитектура x86_64
