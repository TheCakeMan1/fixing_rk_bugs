# 📷 CSI Camera (MIPI CSI) — RK3588

На платформе RK3588 (например, ROCK 5B) может возникать проблема при работе с CSI-камерами (подключаемыми через MIPI-CSI): изображение отображается с зелёным оттенком.

Было замечено на ядре _Linux 5.10.160-rockchip-rk3588_

# 🛠 Решение

Для устранения проблемы необходимо установить следующие пакеты:

```bash
sudo dpkg -i camera_engine_rkaiq_rk3588_1.0.3_arm64.deb
sudo dpkg -i camera_engine_rkaiq_rk3588_update_arm64.deb
sudo dpkg -i camera_engine_rkisp-v2.2.0_arm64.deb
sudo reboot
```

После перезагрузки камера будет работать стабильно с корректной цветопередачей.

# ⚠️ Возможные предупреждения

При использовании GStreamer или FFmpeg может появляться сообщение об ошибке v4l2:

```bash
libv4l2: error getting pixformat: Invalid argument
```

🟢 На практике это не влияет на работу приложений — видео- и фотопоток продолжают обрабатываться корректно.

# 📂 Описание файлов

- camera_engine_rkaiq_rk3588_1.0.3_arm64.deb – базовый движок ISP (Image Signal Processor) для камеры.

- camera_engine_rkaiq_rk3588_update_arm64.deb – обновление с исправлениями и оптимизациями.

- camera_engine_rkisp-v2.2.0_arm64.deb – компонент управления обработкой изображения на уровне RKISP (Rockchip ISP).
