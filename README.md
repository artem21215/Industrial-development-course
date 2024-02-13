[![VK][vk-shield]][vk-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="images/logo.jpg" alt="Logo" width="800" height="800">
  </a>

  <h1 align="center">Управление производственным процессом разработки ПО</h1>

</div>

<!-- TABLE OF CONTENTS -->
<a name="course-introduction"></a>
<details>
  <summary>Содержание</summary>
  <ol>
    <li>
      <a href="#introduction">Введение</a>
    </li>
     <li>
      <a href="#dev-requrements">Требования к разработке</a>
    </li>  
    <li><a href="#git">Git</a></li>
      <ul>
        <li><a href="#git-init-locally">Создание локального git репозитория</a></li>
        <li><a href="#git-init-remote">Работа с удаленным git репозиторием</a></li>
        <li><a href="#git-introduction">Краткий экскурс по основным командам</a></li>
      </ul>
    <li><a href="#unit-testing">Юнит тесты</a></li>
    <li><a href="#continuous-integration">Continuous integration</a></li>
    <li><a href="#project-hierarchy-and-building">Project hierarchy and building</a></li>
    <li><a href="#automatically-generated-documentation">Automatically generated documentation</a></li>
    <li><a href="#static-code-analyzation">Static code analyzation</a></li>
  </ol>
</details>



<!-- Введение -->
<a name="introduction"></a>
## Введение

В рамках данного курса вам предлагается познакомиться с промышленной разработкой и попробовать себя в роли DevOps, Developer, QA.

 Для введения в предметную область - вам необходимо выполнить лабораторные работы. Задача на лабораторные работы - реализовать мини версию проекта, используя практики промышленной разработки.

* Цель лабораторных работ — изучение инструментария и практик, применяющихся при разработке программного обеспечения.

В результате данного курса вам необходимо реализовать законченный проект, включающий в себя:

1. Приложение, разработанное в соответствии с заданием.
2. Систему сборки.
3. Unit-тесты.
4. Настроенные автоматические сборки (CI).
5. Автоматичекую документацию.
6. Отслеживание задач с помощью системы багтрекинга.

Работа над проектом разбивается на короткие итерации. Процесс разработки должен быть зафиксирован в системе контроля версий (git). Проект должен быть опубликован на Github (можно Gitlab, Bitbucket).

* Цель курсовой работы — разработка законченного программного продукта. При этом важно отличать программу от программного продукта.

`Программный продукт` — программа, которую любой человек может запускать, тестировать, исправлять и развивать. Такая программа должна быть написана в обобщенном стиле. В частности, диапазон и вид входных данных должны быть настолько обобщенными, насколько это допускается базовым алгоритмом. Затем программа должна быть тщательно протестирована. Наконец, развитие программы в программный продукт требует создания подробной документации.

**Пример недопустимого кода в программном продукте:**
 ```c++
 FILE *dict = fopen("/home/v.pupkin/myproject/dict.txt", "r");
   ```

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- Требования -->
<a name="dev-requrements"></a>
## Требования к разработке <a name="course-requirements"></a>

_Данные требования - обязательны в промышленной разработке. Код должен быть максимально общим, простым, понятным и достаточно эффективным._

1. Необходимо следовать code style соглашениям. В приоритете использование Google code style для вашего языка программирования, при большом желании можно выбрать другие соглашения, некоторые из них:
  <br>`Google C++ Style Guide` https://google.github.io/styleguide/cppguide.html
  <br>`PEP 7` https://www.python.org/dev/peps/pep-0007/
  <br>`Qt Coding Style` https://wiki.qt.io/Qt_Coding_Style
  
2. Необходимо настроить clang-format для автоматического форматирования.
  <br>_Позже будет проверяться с помощью статических анализаторов кода._
3. Соблюдать консистентность кода в рамках проекта.
4. Чтение документации к используемым инструментам и использование по современным стандартам.
5. Терминал - наше все. Стараться использовать его по максимуму.
<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- Git -->
<a name="git"></a>
## Git

**Рекомендуется к прочтению: <a href="https://git-scm.com/book/en/v2">Pro Git</a>**
<a name="git-init-locally"></a>
### Создание локального git репозитория
```sh
$ cd <path-to-project>
$ mkdir <project-name>
$ cd <project-name>
$ git init <git-repository-name> 
$ echo "# <git-repository-name>" >> README.md
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git branch -M master
```

<a name="git-init-remote"></a>
### Работа с удаленным git репозиторием
- [x] Создать и прокинуть ssh public ключик в удаленный репозиторий. (В github: Settings -> SSH and GPG keys -> New SSH key). Необходимо для синхронизации с удаленным репозиторием по протоколу SSH.

```sh
$ git remote add origin git@github.com:user-name/project-name.git
$ git push -u origin master
```

<a name="git-introduction"></a>
### Краткий экскурс по основным командам
<br>`git status` - Посмотреть текущую информацию об изменении в вашем репозитории. (staged/unstaged, tracked/untracked)
<br>`git add <path-to-file>` - Добавить файл в staging. Удобно пользоваться **Git gui** утилитой для просмотра текущих изменений и добавлении их в staging стадию(готовность к созданию коммита).
<br>`git commit` - Создать коммит. Удобно использовать git commit -m "commit content"
<br>`git branch <branch-name>` - Создать ветку под именем branch-name, указывающую на HEAD. 
<br>`git checkout <branch-name>` - Переместиться на ветку branch-name.
<br>_P.S. Удобно использовать `git checkout -b <branch-name>` для создания новой ветки и перехода на нее одной командой._
<br>`git fetch` - 
<br>`git merge` - 
<br>`git pull` - 
<br>`git cherry-pick` - 
<br>`git rebase` - 

### Требования к оформлению коммитов
Коммит должен быть ...
 

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- Unit testing -->
## Unit testing

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- -->
## Continuous integration

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- -->
## Project hierarchy and building

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- -->
## Bug/Task tracking

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- -->
## Automatically generated documentation

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- -->
## Static code analyzation

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Use this space to list resources you find helpful and would like to give credit to. I've included a few of my favorites to kick things off!

* [Choose an Open Source License](https://choosealicense.com)
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [Malven's Flexbox Cheatsheet](https://flexbox.malven.co/)
* [Malven's Grid Cheatsheet](https://grid.malven.co/)
* [Img Shields](https://shields.io)
* [GitHub Pages](https://pages.github.com)
* [Font Awesome](https://fontawesome.com)
* [React Icons](https://react-icons.github.io/react-icons/search)

<p align="right">(<a href="#course-introduction">к содержанию</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[vk-shield]: https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge&logo=vk&logoColor=violet&label=vklabel&labelColor=green&color=blue&link=https%3A%2F%2Fvk.com%2Fid270206159
[vk-url]: https://vk.com/id270206159
[product-screenshot]: images/screenshot.png