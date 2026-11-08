# АИС «Гостиничный комплекс» — ПР5

**Вариант 12.** Репозиторий демонстрирует организацию командной разработки по Git Flow.

## Структура
- `src/` — исходный код модулей АИС.
- `tests/` — модульные и интеграционные тесты.
- `docs/GIT_FLOW.md` — модель ветвления и жизненный цикл задачи.
- `docs/CODE_REVIEW.md` — регламент и чек-лист проверки кода.
- `.github/PULL_REQUEST_TEMPLATE.md` — шаблон Pull Request.
- `.github/ISSUE_TEMPLATE/feature.yml` — шаблон задачи.

## Модель ветвления
`main` — стабильная версия; `develop` — интеграционная ветка; `feature/*` — разработка функций; `release/*` — подготовка релиза; `hotfix/*` — срочные исправления.

## Роли
**Developer** создаёт feature-ветки, пишет код и тесты, оформляет коммиты и исправляет замечания. **Tech Lead** контролирует архитектуру, защищает основные ветки, проводит финальный аудит PR и утверждает слияние.

## Пример работы
```bash
git switch develop
git pull origin develop
git switch -c feature/hotel-12-skud
git add .
git commit -m "feat(skud): add RFID card validation"
git push -u origin feature/hotel-12-skud
```
Затем создаётся PR из `feature/hotel-12-skud` в `develop`. После успешных CI-проверок и Code Review Tech Lead выполняет Squash and Merge.

Для слияния требуются минимум два одобрения участников команды и финальное одобрение Tech Lead.

**Важно:** это организационный каркас для ПР5. Исходный код приложения и тесты нужно добавлять отдельно; пустые каталоги `src/` и `tests/` сохранены файлами `.gitkeep`.
