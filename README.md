# lab04
# lab04
## Laboratory work IV

Данная лабораторная работа посвещена изучению систем непрерывной интеграции на примере сервиса **Travis CI**

```sh
$ open https://travis-ci.org
```

## Tasks

- [ ] 1. Авторизоваться на сервисе **Travis CI** с использованием **GitHub** аккаунта
- [ ] 2. Создать публичный репозиторий с названием **lab04** на сервисе **GitHub**
- [ ] 3. Ознакомиться со ссылками учебного материала
- [ ] 4. Включить интеграцию сервиса **Travis CI** с созданным репозиторием
- [ ] 5. Получить токен для **Travis CLI** с правами **repo** и **user**
- [ ] 6. Получить фрагмент вставки значка сервиса **Travis CI** в формате **Markdown**
- [ ] 7. Выполнить инструкцию учебного материала
- [ ] 8. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```sh
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GITHUB_TOKEN=<полученный_токен>
```

```sh
$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
$ source scripts/activate
```

```sh
$ \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
$ . scripts/activate
$ rvm autolibs disable
$ rvm install ruby-2.4.2
$ rvm use 2.4.2 --default
$ gem install travis
```

```sh
$ git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab04
$ cd projects/lab04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab04
```

```sh
$ cat > .travis.yml <<EOF
language: cpp
EOF
```

```sh
$ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
```

```sh
$ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
```

```sh
$ travis login --github-token ${GITHUB_TOKEN}
```

```sh
$ travis lint
```

```sh
$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
```

```sh
$ git add .travis.yml
$ git add README.md
$ git commit -m"added CI"
$ git push origin master
```

```sh
$ travis lint
$ travis accounts
$ travis sync
$ travis repos
$ travis enable
$ travis whatsup
$ travis branches
$ travis history
$ travis show
```

## Report

```sh
$ popd
$ export LAB_NUMBER=04
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```
## Homework

Вы продолжаете проходить стажировку в "Formatter Inc." (см [подробности](https://github.com/tp-labs/lab03#Homework)).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы **CMake**.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в [прошлый раз](https://github.com/tp-labs/lab03#Homework). Настройте сборочные процедуры на различных платформах:
* используйте [TravisCI](https://travis-ci.com/) для сборки на операционной системе **Linux** с использованием компиляторов **gcc** и **clang**;
* используйте [AppVeyor](https://www.appveyor.com/) для сборки на операционной системе **Windows**.


```sh
$ mkdir lab04
$ cd lab04
$ git init
подсказка: Using 'master' as the name for the initial branch. This default branch name
подсказка: is subject to change. To configure the initial branch name to use in all
подсказка: of your new repositories, which will suppress this warning, call:
подсказка: 
подсказка: 	git config --global init.defaultBranch <name>
подсказка: 
подсказка: Names commonly chosen instead of 'master' are 'main', 'trunk' and
подсказка: 'development'. The just-created branch can be renamed via this command:
подсказка: 
подсказка: 	git branch -m <name>
Инициализирован пустой репозиторий Git в /home/alina/lab04/.git/
$ git add .
$ git commit -m "lab03"
[master (корневой коммит) 90ecc35] lab03
 108 files changed, 10627 insertions(+)
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CMakeCCompiler.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CMakeCXXCompiler.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CMakeDetermineCompilerABI_C.bin
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CMakeDetermineCompilerABI_CXX.bin
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CMakeSystem.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CompilerIdC/CMakeCCompilerId.c
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CompilerIdC/a.out
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CompilerIdCXX/CMakeCXXCompilerId.cpp
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/3.22.1/CompilerIdCXX/a.out
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/CMakeDirectoryInformation.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/CMakeOutput.log
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/Makefile.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/cmake.check_cache
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/formatter_ex_lib.dir/DependInfo.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/formatter_ex_lib.dir/cmake_clean_target.cmake
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/formatter_ex_lib.dir/compiler_depend.ts
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/formatter_ex_lib.dir/formatter_ex.cpp.o
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/formatter_ex_lib.dir/link.txt
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/formatter_ex_lib.dir/progress.make
 create mode 100644 formatter_ex_lib/_build/CMakeFiles/progress.marks
 create mode 100644 formatter_ex_lib/_build/Makefile
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/CMakeDirectoryInformation.cmake
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/DependInfo.cmake
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/build.make
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/cmake_clean.cmake
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/cmake_clean_target.cmake
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/compiler_depend.make
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/compiler_depend.ts
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/depend.make
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/flags.make
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/formatter.cpp.o
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/formatter.cpp.o.d
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/link.txt
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/formatter_lib.dir/progress.make
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/CMakeFiles/progress.marks
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/Makefile
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/cmake_install.cmake
 create mode 100644 formatter_ex_lib/_build/formatter_lib_dir/libformatter_lib.a
 create mode 100644 formatter_ex_lib/_build/libformatter_ex_lib.a
 create mode 100644 formatter_ex_lib/formatter_ex.cpp
 create mode 100644 formatter_ex_lib/formatter_ex.h
 create mode 100644 formatter_lib/_build/CMakeCache.txt
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CMakeCCompiler.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CMakeCXXCompiler.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CMakeDetermineCompilerABI_C.bin
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CMakeDetermineCompilerABI_CXX.bin
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CMakeSystem.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CompilerIdC/CMakeCCompilerId.c
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CompilerIdC/a.out
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CompilerIdCXX/CMakeCXXCompilerId.cpp
 create mode 100644 formatter_lib/_build/CMakeFiles/3.22.1/CompilerIdCXX/a.out
 create mode 100644 formatter_lib/_build/CMakeFiles/CMakeDirectoryInformation.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/CMakeOutput.log
 create mode 100644 formatter_lib/_build/CMakeFiles/Makefile.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/Makefile2
 create mode 100644 formatter_lib/_build/CMakeFiles/TargetDirectories.txt
 create mode 100644 formatter_lib/_build/CMakeFiles/cmake.check_cache
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/DependInfo.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/build.make
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/cmake_clean.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/cmake_clean_target.cmake
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/compiler_depend.make
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/compiler_depend.ts
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/depend.make
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/flags.make
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/formatter.cpp.o
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/formatter.cpp.o.d
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/link.txt
 create mode 100644 formatter_lib/_build/CMakeFiles/formatter_lib.dir/progress.make
 create mode 100644 formatter_lib/_build/CMakeFiles/progress.marks
 create mode 100644 formatter_lib/_build/Makefile
 create mode 100644 formatter_lib/_build/libformatter_lib.a
 create mode 100644 formatter_lib/formatter.cpp
 create mode 100644 formatter_lib/formatter.h
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CMakeCCompiler.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CMakeCXXCompiler.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CMakeDetermineCompilerABI_C.bin
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CMakeDetermineCompilerABI_CXX.bin
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CMakeSystem.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CompilerIdC/CMakeCCompilerId.c
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CompilerIdC/a.out
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CompilerIdCXX/CMakeCXXCompilerId.cpp
 create mode 100644 hello_world_application/_build/CMakeFiles/3.22.1/CompilerIdCXX/a.out
 create mode 100644 hello_world_application/_build/CMakeFiles/CMakeDirectoryInformation.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/CMakeOutput.log
 create mode 100644 hello_world_application/_build/CMakeFiles/Makefile.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/example.dir/DependInfo.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/example.dir/cmake_clean.cmake
 create mode 100644 hello_world_application/_build/CMakeFiles/example.dir/compiler_depend.make
 create mode 100644 hello_world_application/_build/CMakeFiles/example.dir/compiler_depend.ts
 create mode 100644 hello_world_application/_build/CMakeFiles/example.dir/link.txt
 create mode 100644 hello_world_application/_build/CMakeFiles/example.dir/progress.make
 create mode 100644 hello_world_application/_build/CMakeFiles/progress.marks
 create mode 100644 hello_world_application/_build/Makefile
 create mode 100644 hello_world_application/_build/libformatter_ex_lib.a
 create mode 100644 hello_world_application/_build/libformatter_lib.a
 create mode 100644 hello_world_application/hello_world.cpp
 create mode 100644 solver_application/equation.cpp
 create mode 100644 solver_lib/CMakeLists.txt
 create mode 100644 solver_lib/build/CMakeFiles/3.22.1/CMakeCXXCompiler.cmake
 create mode 100644 solver_lib/build/CMakeFiles/3.22.1/CompilerIdCXX/CMakeCXXCompilerId.cpp
 create mode 100644 solver_lib/build/CMakeFiles/CMakeDirectoryInformation.cmake
 create mode 100644 solver_lib/build/CMakeFiles/CMakeOutput.log
 create mode 100644 solver_lib/build/CMakeFiles/progress.marks
 create mode 100644 solver_lib/build/Makefile
 create mode 100644 solver_lib/build/libsolver_lib.a
 create mode 100644 solver_lib/solver.cpp
 create mode 100644 solver_lib/solver.h
$ git remote add origin https://github.com/Alinoos/lab04.git
$ git push origin master
Username for 'https://github.com': Alinoos
Password for 'https://Alinoos@github.com': 
Перечисление объектов: 105, готово.
Подсчет объектов: 100% (105/105), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (97/97), готово.
Запись объектов: 100% (105/105), 46.28 КиБ | 5.78 МиБ/с, готово.
Всего 105 (изменений 38), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (38/38), done.
remote: 
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/Alinoos/lab04/pull/new/master
remote: 
To https://github.com/Alinoos/lab04.git
 * [new branch]      master -> master
 
$ mkdir .github
$ cd ~/lab04/.github
$ mkdir workflows
$ cd ~/lab04/.github/workflows
$ cat >> Linux.yml << EOF
> EOF
$ nano Linux.yml

name: CMake

on:
 push:
  branches: [master]
 pull_request:
  branches: [master]

jobs: 
 build_Linux:

  runs-on: ubuntu-latest

  steps:
  - uses: actions/checkout@v3

  - name: Configure Solver
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build

  - name: Build Solver
    run: cmake --build ${{github.workspace}}/solver_application/build

  - name: Configure HelloWorld
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build

  - name: Build HelloWorld
    run: cmake --build ${{github.workspace}}/hello_world_application/buildс
$ git add Linux.yml
$ git commit -m "Linux.yml - 1"
[master cbf0ab2] Linux.yml - 1
 1 file changed, 27 insertions(+)
 create mode 100644 .github/workflows/Linux.yml
$ git push origin master
Username for 'https://github.com': Alinoos
Password for 'https://Alinoos@github.com': 
Перечисление объектов: 6, готово.
Подсчет объектов: 100% (6/6), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (3/3), готово.
Запись объектов: 100% (5/5), 600 байтов | 600.00 КиБ/с, готово.
Всего 5 (изменений 1), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Alinoos/lab04.git
   90ecc35..cbf0ab2  master -> master


```
## Links

- [Travis Client](https://github.com/travis-ci/travis.rb)
- [AppVeyour](https://www.appveyor.com/)
- [GitLab CI](https://about.gitlab.com/gitlab-ci/)

```
Copyright (c) 2015-2021 The ISC Authors
```
