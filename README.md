<p align="center">
  <img src="https://raw.githubusercontent.com/DedKamal/DuckStation-RPi5-Build/main/banner_rock_edition.png" alt="DuckStation RPi5 Rock Edition Banner" width="90%">
</p>

<h3 align="center">
  ⚡ <b>DuckStation RPi5 — Rock Edition by Ded Kamal</b> ⚡  
</h3>

<p align="center">
  <a href="https://www.raspberrypi.com/">
    <img src="https://img.shields.io/badge/Built_on-Raspberry_Pi_5-red?logo=raspberrypi&logoColor=white">
  </a>
  <a href="https://www.qt.io/">
    <img src="https://img.shields.io/badge/Qt-6.10-green?logo=qt&logoColor=white">
  </a>
  <img src="https://img.shields.io/badge/GCC-14.2.0-blue?logo=gnu&logoColor=white">
  <img src="https://img.shields.io/badge/Powered_by-Ded_Kamal™-purple?logo=github&logoColor=white">
</p>

---

# 🧠 DuckStation on Raspberry Pi 5  
_By Ded Kamal – «Фишки и плюшки от Деда Камала™»_

---

## 🚀 О проекте  

Руками Деда Камала собран и оптимизирован **DuckStation** — эмулятор PlayStation 1,  
на Raspberry Pi 5 под **Debian Trixie ARM64 + GCC 14 + Qt 6.10.0**.  
Проект направлен на полную совместимость и стабильную сборку под новой ARM-архитектурой.  

---

## 🧩 Среда сборки  

- Raspberry Pi 5 (8 GB)  
- Argon One V3 NVMe Case + 512 GB NVMe  
- Debian Trixie ARM64  
- GCC 14.2.0  
- Qt 6.10.0 (ручная сборка в `/usr/local/Qt-6.10.0`)  

---

## 🧰 Команды сборки DuckStation  

```bash
# 1. Подготавливаем окружение
sudo apt install -y cmake ninja-build git pkg-config libpng-dev

# 2. Клонируем проект
git clone https://github.com/stenzek/duckstation.git duckstation-master
cd duckstation-master

# 3. Чиним PNG и исключения (патчи от Деда Камала)
nano src/util/CMakeLists.txt
# добавляем пути к libpng16 и флаг -fexceptions

# 4. Пересоздаём кэш и собираем
rm -rf build && mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make -j4
