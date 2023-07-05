Advanced pipelines using .gitlab-ci.yml

Keywords:

* local

* file

* remote

* template


## include

- local

- file

- remote

- template

С помощью *include* можно включать в ci другие файлы.

При использовании *include* файл можно разбить на более мелкие, когда проекты похожи друг на друга. Можно создать шаблоны и включать их в проекты.

### local
С помощью *local* можно включить файл из локального репозитория. Он должен находиться в той же ветке.
```
stages:
  - build
  - test
  - deploy

include:
  - local: 'configs/build.yaml'
  - local: 'configs/test.yaml'
  - local: 'configs/deploy.yaml'
```

### file
С помощью *file* можно получить доступ к частным проектам на том же экземпляре GitLab из других проектов. Это полезно когда проекты имеют похожие настройки, т.о. можено включить один файл шаблона.
```
include:
  - project: 'devops/ci-setup'
    file: 'tmpls/microservices.yml'
    ref: 'master'
```

### remote
С помощью *remote* можно включить удаленный файл. К этому файлу дб доступ у экземпляра GitLab.
```
include:
  - remote: 'https://site.pl/my.yml'
```

### template
С помощью *template* можно включить шаблоны , поставляемые с GitLab.
```
include:
  - template: 'Bash.gitlab-ci.yml'
```


## extends

С помощью *extends* можно наследовать информацию о других заданиях в основном задании.

```
.deploy:
  script: ./deploy.sh

deploy dev:
  extends: .deploy

deploy prod:
  extends: .deploy
  when: manual
```

```
test:
  before_script:
    - echo "before"
  script:
    - echo "test"

second test:
  extends: test
  after_script:
    - echo "after"
```

Также можно объединять хэши (но не массивы(!)).
```
example:
  variables:
    MY_VAR: "54"

second example:
  extends: example
  variables:
    MY_SECOND_VAR: "49"
```

## rules

С помощью *rules* можно включать или исключать задания в конвейере. Нельзя включать и исключать одновременно в одном задании.

С помощью *rules* можно указать 2 атрибута (# when, allow_failure), когда произойдет сбой и разрешить его.

* if

* changes

* exists

### if
```
build:
  rules:
    - if: '$CI_COMMIT_REF_NAME == "master"'
      when: always
    - when: manual
      allow_failure: true
```
### changes
*changes* показ, были ли изменены файлы при внесении изменений.

При исп *changes* можно создать или скрыть задание на основе массива файлов или каталогов.

Этот пример показ, что задание запустится только в том случае, если что-то было изменено в Dockerfile или каталоге app/. Если изменений не произойет или изменения будут внесены в другие файлы (#в README.md), то задание не запустится.
```
build:
  rules:
    - changes:
        - Dockerfile
        - app/**/*
```
### exists
*exists* показ, существуют ли конкретные файлы.
При наличии файла Dockerfile задание запускается.
```
build:
  rules:
    - exists:
        - Dockerfile
```

### mixes

```
build:
  rules:
    - if: '$CI_COMMIT_REF_NAME == "master"'
      changes:
        - Dockerfile
      when: always
    - when: manual
      allow_failure: true
```

## trigger

С помощью *trigger* можно определить триггер нисходящего конвейера.

Существует 2 типа нисходящих коныейеров:

* multi-project pipelines

* child pipelines


### multi-project pipelines
С помощью *multi-project pipelines* можно запустить конвейер в другом проекте.

По умолч trigger job не дожидается завершения нисходящего конвейера. Как только будет создан нисходящий конвейер

```
trigger job:
  trigger:
    project: my-group/my-project
    branch: master (optional)
    strategy: depend (optional)
```

### child pipelines
С помощью *child pipelines* можно запустить дочерние конвейеры в том же проекте.