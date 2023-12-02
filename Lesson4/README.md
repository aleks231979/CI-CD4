# Домашнее задание по Уроку 4 Troubleshooting (диагностика и решение проблем в CI/CD)

**Ссылка на gitlab_ci.yaml:** https://gitlab.com/ci-cd7655047/4/-/blob/main/.gitlab-ci.yml

## Задание
Сделать локальный шаблон CI и отдельный репозиторий с шаблонами, подключить их к своему основному репозиторию через include.

## Решение к заданию

Создал в том же репозитории файл `local-included-file.yml` с джобой:
```
local included file job:
  script:
    - echo "This is code from the file, which is included localy"
```

Создал другой репозиторий (проект) и разместил в нём файл `remote-included-file.yml` с джобой:
```
remote included file job:
  script:
    - echo "This is code from the file, which is included from another repository"
```

Пробовал двумя инклудами, не получалось. Получилось так:

```
include:
  - remote: https://gitlab.com/ci-cd7655047/5/-/raw/main/remote-included-file.yml
  - local: local-included-file.yml
```

Отработали обе джобы:

![](1.gif)

Попробовал также через токен. Тоже сработало:
```
include:
  remote: 'https://oauth2:glpat-FwzyeNihxYYZjofyE_4E@gitlab.com/ci-cd7655047/5/-/raw/main/remote-included-file.yml'
```
