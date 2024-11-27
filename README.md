

# Решение проблем при установке Docker, WSL и Ubuntu на Windows

## Проблема 1: Ошибка при установке Docker

**Сообщение об ошибке:**
```
Installation failed. One prerequisite is not fulfilled.
We've detected that you have an incompatible version of Windows.
Docker Desktop requires Windows 10 Pro/Enterprise/Home version 19044 or above.
To continue with the installation, upgrade Windows to a supported version and then re-run the installer.
Close
```

**Скриншот ошибки при установке Docker:**  
![Docker_Desktop_Installer_(1)_SJNZ03Eoms](https://github.com/user-attachments/assets/38c94e18-275c-4c88-98b7-b44cb7575a67)

### Причина:
Ошибка возникает, если ваша версия Windows не поддерживается для установки Docker. Docker требует Windows 10 Pro/Enterprise/Home версии 19044 или выше.

### Решение:
Для корректной установки Docker необходимо внести изменения в реестр Windows и обновить операционную систему. Вот пошаговое руководство:

### Шаг 1: Работа с реестром Windows

1. Нажмите `Windows + R` и введите команду `regedit`, чтобы открыть редактор реестра.

2. Перейдите по следующему пути в редакторе реестра:
   
   ```
   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion
   ```

3. Найдите параметры `CurrentBuild` и `CurrentBuildNumber` и убедитесь, что их значения соответствуют версии Windows 10 19044 или выше. Если версия ниже, обновите Windows до поддерживаемой.

**Скриншот работы с реестром:**  
![regedit_nJSRLu3kng](https://github.com/user-attachments/assets/ee0843a4-bdb4-4873-8a53-43fa3fbec1f1)

4. После изменений в реестре и обновления Windows, перезапустите компьютер и повторно запустите установку Docker.

---

## Проблема 2: Не запускается Microsoft Store

Если после внесения изменений в реестр Microsoft Store не работает или не может быть запущен, это может быть связано с отключенными обновлениями или программой **Windows Update Blocker**.

### Шаги для решения:

1. **Проверьте, не блокируют ли обновления вашу систему.** Если у вас установлена программа **Windows Update Blocker**, отключите ее или настройте обновления для Windows.

   Скачайте **Windows Update Blocker** с [официального сайта](https://www.softportal.com/software-45498-windows-update-blocker.html).

2. Убедитесь, что обновления включены в Windows и перезагрузите компьютер.

**Скриншот программы Windows Update Blocker:**  
![image](https://github.com/user-attachments/assets/e048d8d2-2184-48e1-9499-a19906a25b5d)

---

## Проблема 3: Установка WSL и Ubuntu

После того как вы решили проблемы с Docker и Microsoft Store, необходимо настроить WSL для работы с Ubuntu.

### Шаг 1: Включение виртуализации (Hyper-V)

Docker и WSL требуют включенной виртуализации. Для этого выполните следующие шаги:

1. Скачайте и запустите файл `InstallHyperV.bat`, который находится в этом репозитории. Этот скрипт включит поддержку Hyper-V.

2. После этого перезагрузите компьютер.

### Шаг 2: Включение виртуализации в BIOS

Для работы с WSL и Docker необходимо также включить аппаратную виртуализацию в BIOS. 

- Перезагрузите компьютер и войдите в настройки BIOS.
- Найдите и включите опцию виртуализации (обычно называется **Intel VT-x** или **AMD-V**).

Полное руководство по включению виртуализации в BIOS можно найти [здесь](https://support.bluestacks.com/hc/ru/articles/360059063711-Как-включить-аппаратную-виртуализацию-VT-в-BIOS-на-Windows-7-для-BlueStacks-5).

### Шаг 3: Установка Ubuntu через Microsoft Store

1. Перейдите в **Microsoft Store** и найдите **Ubuntu**.
2. Установите Ubuntu, после чего должна автоматически настроиться среда WSL.

Если установка Ubuntu вызывает ошибку, возможно, необходимо выполнить следующие действия:

### Шаг 4: Установка всех обновлений Windows

1. Перейдите в **Настройки** -> **Обновления и безопасность** -> **Центр обновления Windows**.
2. Нажмите **Проверить наличие обновлений** и установите все доступные обновления.

**Скриншот ошибки при установке Docker (не запускается после обновления):**  
![image](https://github.com/user-attachments/assets/13b6d957-d812-4740-b83f-b5c327b1fca3)

После установки всех обновлений и перезагрузки системы, снова попробуйте установить Ubuntu.

---

## Заключение

Этот файл README поможет вам решить основные проблемы при установке Docker, WSL и Ubuntu на Windows. Следуя этим шагам, вы сможете:

- Исправить ошибку, связанную с несовместимой версией Windows для установки Docker.
- Внести изменения в реестр для корректной работы Docker.
- Включить виртуализацию для работы с WSL.
- Установить Ubuntu через Microsoft Store.

После выполнения всех шагов не забудьте перезагрузить компьютер. Если проблемы продолжают возникать, убедитесь, что все обновления Windows установлены, и повторите установку.

---

## Дополнительные источники:

- [Документация по установке Docker на Windows](https://github.com/BrainStorm-commits/Docker-installation-Windows10Home)
- [Официальное руководство по установке WSL от Microsoft](https://learn.microsoft.com/ru-ru/windows/wsl/install)

---
