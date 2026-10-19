# Квест 2: Диагностика Nginx через systemd

**Что сделал:** Специально удалил `;` в `/etc/nginx/nginx.conf`.
**Симптом:** `systemctl restart nginx` не выдаёт явной ошибки в терминале, но сервис не работает.
**Диагностика:** 
- `systemctl status nginx` показал статус `failed`.
- `journalctl -u nginx -n 20` показал точную ошибку: `nginx: [emerg] invalid number of arguments in "worker_processes" directive in /etc/nginx/nginx.conf:2`.
**Решение:** Вернул `;` в конец строки, сделал `systemctl restart nginx`. Всё заработало.
**Вывод:** `systemctl status` даёт общую картину, а `journalctl` показывает конкретную строку и причину падения.
