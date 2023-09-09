# Настройка окружения для работы с ОС Pintos

```text
Окружение для компиляции и запуска pintos может быть подготовлено только на базе одной 
из операционных систем Linux. Исполняемый образ ОС Pintos может быть запущен на эмуляторе 
программного обеспечения, таком как Bochs, QEMU, или VMWare Player. Данные эмуляторы 
являются независимыми программными продуктами, т.к. не представлены в исходных кодах ОС 
Pintos и на поставляются вместе с ними. Данное руководство подразумевает, что настройка 
окружения производится на Linux Ubuntu 16.04, но с некоторыми изменениями оно будет 
справедливо для любой версии операционной системы семейства Debian.
```

## 1. Необходимо убедиться, что в системе присутствуют все необходимые пакеты, необходимые для сборки и запуска ОС pintos следующей командой:

```shell
sudo apt-get install gcc-multilib make perl qemu
```

```text
В данной команде контекст sudo требует запуска от имени суперпользователя (необходимое 
условие для утилиты установки apt-get). В результате выполнения команды для ОС Linux Ubuntu 
16.04 будет установлена версия компилятора gcc 5.4.0, эмулятор qemu 2.5.0.
```

*Примечание: если установлена 32-разрядная система Linux, то вместо пакета gcc-multilib
следует устанавливать пакет gcc.*

## 2. Эмулятор qemu содержит несколько бинарных файлов для эмуляции систем различных архитектур. Все бинарные файлы располагаются в каталоге /usr/bin/. Скрипты, входящие в ОС Pintos, запускают эмулятор командой "qemu", без указания конкретной системы эмуляции. Поэтому для корректной работы скриптов pintos требуется создать ссылку, указывающую какой именно бинарный файл будет запускаться по команде "qemu".

```shell
sudo ln /usr/bin/qemu-system-x86_64 /usr/bin/qemu
```

_Примечение: если установлена 32-разрядная система Linux, то вместо qemu-system-x86_64
следует использовать qemu-system-x86._