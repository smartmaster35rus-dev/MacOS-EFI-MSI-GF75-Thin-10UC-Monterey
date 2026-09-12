<div align="center">

# MacOS EFI · MSI GF75 Thin 10UC

### OpenCore · macOS Monterey 12.x · Platinum Edition

[![OpenCore](https://img.shields.io/badge/OpenCore-EFI-6C5CE7?style=for-the-badge&logo=apple&logoColor=white)](https://github.com/acidanthera/OpenCorePkg)
[![macOS](https://img.shields.io/badge/macOS-Monterey%2012.x-000000?style=for-the-badge&logo=apple&logoColor=white)](https://www.apple.com/macos/monterey/)
[![Laptop](https://img.shields.io/badge/MSI-GF75%20Thin%2010UC-FF6B00?style=for-the-badge&logo=msi&logoColor=white)](https://www.msi.com/)
[![License](https://img.shields.io/badge/License-MIT-2ECC71?style=for-the-badge)](LICENSE)
[![Release](https://img.shields.io/badge/Download-v1.0.0-E74C3C?style=for-the-badge&logo=github&logoColor=white)](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC-Monterey/releases/latest)

**Готовый EFI-загрузчик Hackintosh для MSI GF75 Thin 10UC-048XRU**  
*Intel Comet Lake · UHD 630 · RTX 3050 · AX201 Wi-Fi 6*

[Скачать релиз](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC-Monterey/releases/latest) · [Руководство OpenCore](https://dortania.github.io/OpenCore-Install-Guide/) · [Sonoma EFI](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC) · [Сообщить о проблеме](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC-Monterey/issues)

</div>

---

## Обзор

| | |
|---|---|
| **Последний релиз** | [**v1.0.0 — Releases**](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC-Monterey/releases/latest) |
| **Архив** | `MacOS-EFI-MSI-GF75-Thin-10UC-Monterey-v1.0.0.zip` |
| **Загрузчик** | OpenCore |
| **macOS** | Monterey 12.x |
| **SMBIOS** | MacPro7,1 |
| **Тема OpenCore** | Acidanthera GoldenGate |
| **boot-args** | `-v npci=0x2000 alcid=7` |

> Для **macOS Sonoma 14.5** используйте отдельный репозиторий: [MacOS-EFI-MSI-GF75-Thin-10UC](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC)

---

## Конфигурация

| Компонент | Характеристики |
|-----------|----------------|
| **Модель** | MSI GF75 Thin 10UC-048XRU 17.3" (RTX 3050) |
| **Процессор** | Intel® Core™ i5-10500H @ 2.50 GHz |
| **Память** | 16 GB DDR4 3200 MHz (8+8) |
| **Диск** | M.2 PCIe SSD Kingston OM8PCP3512F 512 GB |
| **iGPU** | Intel UHD Graphics 630 |
| **dGPU** | NVIDIA GeForce RTX 3050 4 GB *(не используется в macOS)* |
| **Ethernet** | Realtek RTL8168H |
| **Дисплей** | IPS FHD 1920×1080 (17.3") @ 144 Hz |
| **Аудио** | Realtek ALC233 (`alcid=7`) |
| **Wi-Fi** | Intel® Wi-Fi 6 AX201 |
| **Bluetooth** | Intel AX201 |

---

## Настройки BIOS

| Параметр | Значение |
|----------|----------|
| Скрытые настройки | `Ctrl Right` + `Shift Right` + `Alt Left` + `F2` |
| Secure Boot | **Выключить** → `Security` |
| CFG Lock | **Выключить** → `Advanced → Power & Performance → CPU → CPU Lock Configuration` |
| Fast Boot | **Выключить** → `Boot` |
| Режим загрузки | **UEFI без CSM** → `Boot` |

---

## Совместимость

### Работает

| Категория | Статус |
|-----------|--------|
| QE/CI графика iGPU Intel UHD 630 | ✅ |
| Управление питанием процессора | ✅ |
| Перезагрузка, сон и выключение | ✅ |
| Аудио Realtek ALC233 | ✅ |
| Ethernet Realtek RTL8168H | ✅ |
| Состояние батареи | ✅ |
| Все USB-порты | ✅ |
| HDMI видео/аудио | ✅ |
| iMessage / FaceTime | ✅ |

### Не работает / ограничения

| Функция | Статус |
|---------|--------|
| AirDrop | ❌ |
| NVIDIA RTX 3050 | ❌ *(не поддерживается в macOS)* |

---

## Структура репозитория

```
├── BOOT/                  # Загрузчик BOOTx64.efi
├── OC/
│   ├── ACPI/              # SSDT + DSDT таблицы
│   ├── Drivers/           # OpenCore-драйверы
│   ├── Kexts/             # Кернел-расширения
│   ├── Resources/         # Тема OpenCore (GoldenGate)
│   ├── Tools/             # Утилиты OpenCore
│   └── config.plist       # Основной конфиг
├── LICENSE
└── README.md
```

---

## ACPI (SSDT)

| Файл | Назначение |
|------|------------|
| `DSDT.aml` | Патченная DSDT |
| `SSDT-EC.aml` | Виртуальный EC |
| `SSDT-HPET.aml` | Исправление HPET |
| `SSDT-IMEI.aml` | IMEI |
| `SSDT-PMC.aml` | PMC |
| `SSDT-CPUM.aml` | CPU power management |
| `SSDT-DTGP.aml` | DTGP |
| `SSDT-SBUS-MCHC.aml` | SMBus |
| `SSDT-UNC.aml` | UNC |
| `SSDT-RTC0-RANGE-HEDT.aml` | RTC |
| `SSDT-USB-Reset.aml` | USB reset |

---

## Kexts

| Kext | Назначение |
|------|------------|
| Lilu | Патч-инжектор (базовый) |
| VirtualSMC | Эмуляция SMC |
| SMCProcessor | Температура процессора |
| SMCSuperIO | Super I/O |
| WhateverGreen | Графика Intel iGPU |
| AppleALC | Аудио Realtek ALC233 |
| RealtekRTL8111-v2.2.2 / v2.4.2 | Ethernet RTL8168H |
| NVMeFix | NVMe SSD |
| USBMap | Карта USB-портов |
| FeatureUnlock | Разблокировка функций |
| RadeonSensor | Датчики AMD GPU |
| SMCRadeonGPU | SMC для AMD GPU |
| VoodooTSCSync | Синхронизация TSC |
| AirportBrcmFixup | Wi-Fi (Broadcom) |
| RtWlanU / RtWlanU1827 | Wi-Fi (Realtek USB) |

---

## OpenCore Drivers

| Драйвер | Назначение |
|---------|------------|
| OpenRuntime.efi | Runtime services |
| OpenCanopy.efi | Графический интерфейс загрузки |
| HfsPlus.efi | Поддержка HFS+ |
| AudioDxe.efi | Звук в OpenCore |
| ResetNvramEntry.efi | Сброс NVRAM |
| CrScreenshotDxe.efi | Скриншоты |
| OpenLinuxBoot.efi | Загрузка Linux |
| ext4_x64.efi | ext4 |

---

## Установка

### Быстрый старт

1. Скачайте [**последний релиз**](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC-Monterey/releases/latest)
2. Распакуйте ZIP-архив
3. Смонтируйте EFI-раздел (через [MountEFI](https://github.com/corpnewt/MountEFI) или `diskutil mount` в macOS)
4. Скопируйте папку `EFI` из архива на EFI-раздел
5. Настройте BIOS по таблице выше
6. Перезагрузитесь и выберите macOS в OpenCore

### Сборка из репозитория

```bash
git clone https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC-Monterey.git
# Скопируйте BOOT и OC в EFI/ на ESP-разделе:
#   EFI/BOOT/  ← BOOT/
#   EFI/OC/    ← OC/
```

> Перед использованием сгенерируйте **уникальные** SMBIOS, Serial Number и ROM для iMessage/FaceTime.  
> Руководство: [Dortania — Post-Install](https://dortania.github.io/OpenCore-Post-Install/)

---

## Важно

- **RTX 3050** не поддерживается в macOS — используется только Intel UHD 630
- SMBIOS в конфиге: **MacPro7,1** — замените на уникальные данные перед использованием
- Для Wi-Fi Intel AX201 рекомендуется обновить kexts (AirportItlwm) или использовать Sonoma EFI
- Перед обновлением macOS проверяйте совместимость kexts

---

## Поддержка

- Сайт: [smartmaster35rus.ru](https://smartmaster35rus.ru)
- Telegram: [@SmartMaster35Rus](https://t.me/SmartMaster35Rus)

---

<div align="center">

**© 2026 [smartmaster35rus-dev](https://github.com/smartmaster35rus-dev)**

*Сделано с ♥ для сообщества Hackintosh*

</div>
