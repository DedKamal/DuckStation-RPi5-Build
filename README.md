# 🧠 DuckStation on Raspberry Pi 5  
_By Ded Kamal – “Фишки и плюшки от Деда Камала™”_  

---

## 🚀 О проекте  

Руками Деда Камала собран и оптимизирован DuckStation — эмулятор PlayStation 1,  
на Raspberry Pi 5 под **Debian Trixie + GCC 14 + Qt 6.10**.  

Проект родился из желания сделать полноценную ретро-станцию,  
которая реально летает даже с тяжёлыми играми и современным GUI.  

---

## ⚙️ Среда сборки  

- Raspberry Pi 5 (8 GB)  
- Argon One V3 NVMe Case + 512 GB NVMe  
- Debian Trixie ARM64  
- GCC 14.2.0  
- Qt 6.10.0 (ручная сборка в `/usr/local/Qt-6.10.0`)  

---

## 🧩 Команды сборки DuckStation  

```bash
# 1. Подготавливаем окружение
sudo apt install -y cmake ninja-build g++ git qt6-base-dev qt6-tools-dev-tools

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
