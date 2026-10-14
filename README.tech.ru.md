<p align="right"><b>Русская техническая версия</b> | <a href="./README.ru.md">Краткий README</a></p>

<h1 align="center">Sergey Haeniken</h1>
<p align="center"><b>DevOps / DevSecOps / SRE Engineer</b> · Linux-инфраструктура · Надёжность · Научно-техническое ПО</p>

<p align="center">
  <img src="https://img.shields.io/badge/Опыт-11%2B%20лет-1F8A70?style=for-the-badge" alt="Опыт: 11+ лет" />
  <img src="https://img.shields.io/badge/Фокус-DevOps%20%7C%20DevSecOps%20%7C%20SRE-0A66C2?style=for-the-badge" alt="DevOps, DevSecOps, SRE" />
  <img src="https://img.shields.io/badge/Контуры-Linux%20%7C%20Kubernetes%20%7C%20Docker-3D5A80?style=for-the-badge" alt="Linux, Kubernetes, Docker" />
</p>

## Профиль

Более 11 лет работаю с Linux-инфраструктурой: эксплуатация распределённых сервисов, выпуски, наблюдаемость, сеть, хранилища, разбор инцидентов и защита рабочих контуров.

Пишу инструменты для диагностики, генерации конфигурации, сверки состояния, безопасного повтора операций и обработки научных данных.

## Опыт

- **Банк «Санкт-Петербург» — инженер DevOps, 2024 — настоящее время.** Эксплуатация инфраструктуры интернет-банка: более 100 микросервисов в Docker Swarm, Kubernetes и Helm, GitLab CI/CD, плановые и аварийные развёртывания. Мониторинг критичных интеграций и бизнес-метрик, разбор инцидентов L3, участие в круглосуточном восстановлении сервисов с SLA 99,97%. Сейчас участвую в проекте внедрения ИИ для анализа прикладных журналов и разбора ошибок сервисов.
- **TIPPO Cloud Service — SRE-инженер, 2024 — настоящее время, проектная работа.** Эксплуатация SaaS-инфраструктуры: более 500 клиентских ресурсов, 7 виртуальных и 6 физических серверов, свыше 75 ТБ данных. Сеть WireGuard/IPsec с BGP/BFD, ZFS RAIDZ, MySQL Galera, GitOps для Traefik, Restic/S3 и контрольные восстановления.
- **StormWall — ведущий инженер, 2021—2024.** Защита трафика L3–L7, WAF, GRE/IPIP, разбор сетевых дампов и событий Splunk/R-Vision. Автоматизация диагностики на Ansible, Bash и Python.
- **ElGracia — инфраструктура Linux, 2014—2019.** Платформа примерно на 1000 одновременных пользователей: Linux, MySQL/InnoDB, MariaDB Galera, централизованные журналы, разбор аварийных дампов и поиск причин сбоев на границе инфраструктуры и C++-ядра.

## Основные задачи

- эксплуатация Linux, Kubernetes, Helm, Docker Swarm, Nginx и Traefik;
- CI/CD и GitOps: проверки конфигурации, сборка, миграции, управляемая выкладка и откат;
- наблюдаемость в Zabbix, Grafana, Prometheus, ELK/Kibana и Splunk;
- разбор инцидентов по метрикам, журналам, сетевым дампам, трассировке запросов и планам SQL;
- сеть и отказоустойчивость: WireGuard, IPsec/XFRM, BGP, BFD, FRR, CoreDNS;
- хранилища и базы данных: ZFS, программный RAID, MySQL/MariaDB, PostgreSQL/TimescaleDB, Oracle DB;
- DevSecOps: WAF, сегментация, управление секретами, проверка образов и конфигураций, CrowdSec, Trivy, OpenVAS;
- ранбуки, проверка резервного копирования и контролируемые испытания переключения на резерв.

## Избранные проекты и задачи

### [«Астросферум»](https://github.com/Haeniken/bot_astrosferum)

[Сайт проекта](https://astrosferum.com) · [ORCID 0009-0005-5804-5011](https://orcid.org/0009-0005-5804-5011)

Разработал систему прогноза условий астрономических наблюдений на данных ICON-EU и ICON Global: проверка полноты исходных данных, расчёт атмосферных показателей и графики для Telegram, VK и веб-интерфейса. Результаты сохраняют связь с исходным циклом модели.

В «Астрокуполе» разрабатываю прогноз по 129 направлениям на 72 часа. Развёрнуты расчётное ядро, очередь и интерфейс; до публичного выпуска остаются проверка нагрузки и сверка с наблюдениями. Отказ необязательного источника NASA GEOS-CF не останавливает основной прогноз.

[Расчёты](https://haeniken.com/articles/astrosferum/) · [Архитектура «Астрокупола»](https://haeniken.com/articles/astrodome/)

### Отказоустойчивая сеть из семи узлов

Внедрил полносвязную сеть: WireGuard — основной транспорт, IPsec/XFRM — резерв, FRR с BGP/BFD выбирает маршрут. Написал генератор конфигурации и инструкции по обслуживанию; переключение проверяю прикладными запросами. Zabbix показывает выбранный транспорт и состояние связей.

Для HTTPS добавил переключение между публичным каналом, внутренней сетью и SSH-туннелем. Возврат — после 180 секунд устойчивой доступности; работа через резерв и полный отказ различаются в Zabbix.

[Схема и проверки](https://haeniken.com/articles/network-ha/)

### Мониторинг сервиса конвертации

Настроил Zabbix для Go-сервиса: API, RabbitMQ, обработчики заданий, очереди и внешние зависимости. Контрольная задача проверяет конвертацию, создание превью и операции с файлами. Она выявила отказы загрузки, хотя проверки контейнеров проходили. Доля HTTP-ошибок считается по одновременно снятым счётчикам; зависимости оповещений подавляют каскад сообщений.

### Обслуживание файлового хранилища на Go

Разработал утилиты восстановления записей о файлах в MySQL и дедубликации через жёсткие ссылки без остановки приложения. Потоковое чтение и внешняя сортировка ограничивают память; перед атомарной заменой проверяются файлы, ведётся журнал восстановления. В рабочем контуре выгрузил и отсортировал 96,26 млн строк БД, затем запустил дедубликацию.

### GitOps для Traefik

Разработал [панель управления доменами](https://github.com/Haeniken/gitops-traefik-panel): проверка домена, запрос на слияние в GitHub, проверки конфигурации, выкладка и выпуск TLS-сертификата. Изменения инфраструктуры сохраняются в Git.

### Согласование PostgreSQL и внешних систем

В закрытой панели управления вынес сетевые операции из транзакций PostgreSQL в задания с безопасным повтором. Повторное платёжное уведомление не зачисляет баланс дважды; фоновая сверка восстанавливает записанное состояние на внешних узлах. Подпись HMAC-SHA256, повторная доставка и конфликты проверены тестами.

[Техническая заметка](https://haeniken.com/articles/rabbithole-vpn/)

### Многопоточный TURN-транспорт для WireGuard

Разработал [серверный прокси](https://github.com/Haeniken/rabbithole-turn-proxy) и [Android-клиент](https://github.com/Haeniken/rabbithole-turn-android): несколько TURN/DTLS-потоков образуют одну UDP-сессию с постоянным сокетом до WireGuard. Клиент учитывает задержки и потери, использует TCP как резерв и готовит новые соединения до смены сети. Сохранена совместимость со сторонними клиентами.

[Разбор транспорта](https://haeniken.com/articles/turn-transport/)

### Архитектурный аудит семи узлов

Сверил конфигурации семи рабочих узлов: локальное состояние на ZFS, независимые очереди RabbitMQ и единые точки отказа в мониторинге и резервном копировании. Подготовил план унификации сборок, ролей узлов, очередей и служебной сети. Общую оркестрацию оставил следующим этапом после устранения зависимостей от локальных данных.

### Производительность мониторинга

Локализовал задержки Zabbix и PostgreSQL/TimescaleDB на общих HDD: `iowait` до 86–90%, задержки диска до 300–440 мс. Ограничил фоновый сбор, настроил PostgreSQL и ресурсы веб-интерфейса. Долгосрочное решение — отдельные SSD/NVMe для БД и WAL.

## Инструменты

| Область | Что использую |
|---|---|
| Linux и сеть | Linux, systemd, sysctl, iptables, WireGuard, StrongSwan/IPsec, XFRM, FRR, BGP, BFD, CoreDNS |
| Контейнеры | Kubernetes, Helm, Docker, Docker Swarm, Compose, Traefik, Nginx |
| Автоматизация | Ansible, GitLab CI, GitHub Actions, GitOps, Bash, Python, Go, PHP |
| Наблюдаемость | Zabbix, Grafana, Prometheus, ELK/Kibana, Splunk, R-Vision |
| Данные | MySQL/MariaDB Galera, PostgreSQL/TimescaleDB, Oracle DB, ZFS, Restic, S3 |
| DevSecOps | WAF, CrowdSec, Trivy, OpenVAS, Lynis, rkhunter, управление секретами и проверка конфигураций |
| Научные расчёты | ICON-EU, ICON Global, GRIB2, GEOS-CF, численное интегрирование, WebGL2/Canvas |

## Сертификаты

- [IBM Cybersecurity Analyst Professional Certificate](https://www.coursera.org/account/accomplishments/specialization/certificate/CTF3ZA9TULXG)
- [Security Analyst Fundamentals](https://www.coursera.org/account/accomplishments/specialization/certificate/VFFHAW9QMFZR)
- [IT Fundamentals for Cybersecurity](https://www.coursera.org/account/accomplishments/specialization/certificate/PCRSJGSVCAEH)
- [Cyber Threat Intelligence](https://www.coursera.org/account/accomplishments/certificate/4X9JPCHUZW3P)
- [Network Security & Database Vulnerabilities](https://www.coursera.org/account/accomplishments/certificate/RYBRER3QAF3S)
- [Penetration Testing, Incident Response and Forensics](https://www.coursera.org/account/accomplishments/certificate/8P7UYE98Q8PT)

---

<p align="center"><i>Рассматриваю роли DevOps / DevSecOps / SRE-инженера.</i></p>
