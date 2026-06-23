# 💰 VoidRP Wealth Tax

> Paper 1.21.1 плагин — прогрессивный налог на богатство для балансировки экономики сервера.

![Paper](https://img.shields.io/badge/Paper-1.21.1-00AF54)
![Java](https://img.shields.io/badge/Java-21-ED8B00?logo=openjdk&logoColor=white)
![Vault](https://img.shields.io/badge/depends-Vault-yellow)
![License](https://img.shields.io/badge/license-proprietary-red)

---

## 🗺️ Место в экосистеме

```
  Minecraft Server — economy tick
        │ Vault API (читает баланс)
        ▼
  voidrp-wealth-tax
        │ Vault API (списывает налог)
        ▼
  Казна нации (через gamesync-plugin)
```

Налог автоматически перераспределяет богатство: чем больше у игрока денег, тем выше процент. Собранные средства направляются в казну государства игрока.

---

## ✨ Возможности

- **Прогрессивные ставки** — налог растёт вместе с балансом игрока
- **Автоматическое списание** — по расписанию (настраиваемый интервал)
- **Интеграция с нациями** — собранный налог зачисляется в казну нации
- **Исключения** — возможность освободить игроков/группы от налога
- **Уведомления** — игрок получает сообщение о списанном налоге

---

## 📋 Требования

| Компонент | Версия |
|---|---|
| Paper / Mohist | 1.21.1 |
| Java | 21 |
| Vault | обязательно |

---

## 🚀 Сборка и установка

```bash
cd voidrp_wealth_tax
./gradlew shadowJar
# → build/libs/voidrp-wealth-tax-*.jar
```

1. Скопировать jar в `plugins/`
2. Перезапустить сервер
3. Настроить `plugins/VoidRpWealthTax/config.yml`

---

## ⚙️ Конфигурация

```yaml
# config.yml
interval_minutes: 60        # интервал списания налога
brackets:
  - min: 0
    max: 1000000
    rate: 0.0               # 0% до 1М
  - min: 1000000
    max: 10000000
    rate: 0.005             # 0.5% от 1М до 10М
  - min: 10000000
    max: -1                 # -1 = без верхней границы
    rate: 0.01              # 1% свыше 10М
nation_treasury: true       # зачислять в казну нации
notify_players: true
```

---

## 🔗 Связанные репозитории

| Репо | Связь |
|---|---|
| [voidrp-gamesync-plugin](https://github.com/VOIDRP-MINECRAFT/voidrp-gamesync-plugin) | Получает средства в казну нации |
| [minecraft-backend](https://github.com/VOIDRP-MINECRAFT/minecraft-backend) | Хранит транзакции казны |

---

<div align="center">
<a href="https://void-rp.ru">🌐 Сайт</a> ·
<a href="https://github.com/VOIDRP-MINECRAFT">🏠 Организация</a>
</div>
