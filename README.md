# Домашнее задание к занятию "`8.3. Gitlab`" - `Кузин Максим`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)


![img](https://gitlab.infernofeniks.ru/feniks/gitlab-hw-8-3/-/blob/main/sreenshots/logo.png)

---

### Задание 1

`Сначала зарегистрировал раннер, как специфичный, а потом перевел его shared runner`


![Задание_1.1](https://gitlab.infernofeniks.ru/feniks/gitlab-hw-8-3/-/blob/main/sreenshots/image_1.1.jpg)
![Задание_1.1](https://gitlab.infernofeniks.ru/feniks/gitlab-hw-8-3/-/blob/main/sreenshots/image_1.2.jpg)


---

### Задание 2

`Добавил с скрипт инициализацию mod файла, чтобы тест смог выполниться.`


** .gitlab-ci.yml **
```
stages:
   - test
   - build

test:
  stage: test
  image: golang:1.13
  script: 
   - go mod init feniks
   - go test .

build:
  stage: build
  image: docker:latest
  script:
   - docker build .

```

![Задание_2](https://gitlab.infernofeniks.ru/feniks/gitlab-hw-8-3/-/blob/main/sreenshots/image_2.jpg)


---

### Задание 3


#### Задание 3.1
** .gitlab-ci.yml **
```
stages:
   - work

test:
    stage: work
    image: golang:1.13
    script: 
     - go mod init feniks
     - go test .

build:
    stage: work
    image: docker:latest
    script:
     - docker build .

```


#### Задание 3.2
** .gitlab-ci.yml **
```
stages:
   - test
   - build

test:
  stage: test
  image: golang:1.13
  script:
   - go mod init feniks
   - go test .
  only:
     changes:
       - "*.go"

build:
  stage: build
  image: docker:latest
  script:
   - docker build .

```


![Задание_3.1](https://gitlab.infernofeniks.ru/feniks/gitlab-hw-8-3/-/blob/main/sreenshots/image_3.1.jpg)
![Задание_3.2](https://gitlab.infernofeniks.ru/feniks/gitlab-hw-8-3/-/blob/main/sreenshots/image_3.2.jpg)

