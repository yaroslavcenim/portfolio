journalctl — команда для просмотра логов, собранных systemd-journald.

Основные ключи journalctl:
Логи конкретно юнита: -u "unit" (например nginx)
В реальном времени: -f
В конец (проследние записи): -e
С даты: --since "2026-03-12" или: "1 hour ago" "today" "1 week ago" "9:00" "now"
До даты: --until "2026-03-16" или: "today" "now" "13:00"
Формат вывода: -o (например: json)
Логи ядра: -k
Обратный порядок: -r
Приоритет: -p (Для разных приоритетов: -p 3..5)

Приоритеты:
· 0 — emergency
· 1 — alert
· 2 — critical
· 3 — error
· 4 — warning
· 5 — notice
· 6 — info
· 7 — debug