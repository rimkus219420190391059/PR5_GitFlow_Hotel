# Регламент Git Flow

## Постоянные ветки
| Ветка | Назначение |
|---|---|
| `main` | Стабильная production-версия; прямые коммиты запрещены |
| `develop` | Интеграция завершённых задач |

## Временные ветки
- `feature/<task-id>-<name>` — создаётся от `develop`, сливается в `develop`.
- `release/<version>` — подготовка релиза; после проверки изменения попадают в `main` и `develop`.
- `hotfix/<task-id>-<name>` — срочное исправление от `main`; после проверки изменения попадают в `main` и `develop`.

## Жизненный цикл feature
```bash
git switch develop
git pull origin develop
git switch -c feature/hotel-12-skud
# разработка и локальные тесты
git add .
git commit -m "feat(skud): add RFID card validation"
git push -u origin feature/hotel-12-skud
```
На GitHub создаётся Pull Request: base — `develop`, compare — feature-ветка. В описании указываются задача, изменения, результаты тестирования и самопроверка. После CI и одобрений Tech Lead выполняет Squash and Merge; feature-ветка удаляется.

## Conventional Commits
Формат: `тип(область): описание`.
- `feat` — новая функция;
- `fix` — исправление;
- `test` — тесты;
- `docs` — документация;
- `refactor` — рефакторинг.

## CI/CD и защита веток
Перед слиянием предусматриваются `dotnet build`, `dotnet test` и анализ качества SonarQube (если он подключён к проекту). Для `main` и `develop` следует включить Branch Protection Rules: запрет прямого push, обязательный PR, успешные CI-проверки, отсутствие незакрытых обсуждений и обязательные одобрения.

## Роли
**Developer:** ведёт feature-ветку, реализует функциональность, добавляет тесты, соблюдает формат коммитов и исправляет замечания.

**Tech Lead:** отвечает за архитектуру, защиту `main` и `develop`, финальное утверждение PR, релизные и hotfix-ветки.
