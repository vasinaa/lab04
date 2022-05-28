 # lab04  Васина Александра ИУ8-22
Вы продолжаете проходить стажировку в "Formatter Inc.".

В прошлый раз ваше задание заключалось в настройке автоматизированной системы **CMake**.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в прошлый раз. Настройте сборочные процедуры на различных платформах:
* используйте `GitHub Actions` для сборки на операционной системе **Linux**.





1. Создаём директорию `.github/workflows` и добавляем в неё файл `main.yml`:


```yaml
name: CI

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - name: checkout
      uses: actions/checkout@v3
    
   steps:
    - name: checkout
      uses: actions/checkout@v3
    
    - name: Build *formatter_lib*
      run: |
        cmake -H. -B_build
        cmake --build _build
      shell: bash
      working-directory: formatter_lib
    - name: Build *formatter_ex_lib*
      run: |
        cmake -H. -B_build
        cmake --build _build
      shell: bash
      working-directory: formatter_ex_lib
    - name: Build *hello_world_application*
      run: |
        cmake -H. -B_build
        cmake --build _build
      shell: bash
      working-directory: hello_world_application
      
    - name: Build *solver_application*
      run: |
        cmake -H. -B_build
        cmake --build _build
      shell: bash
      working-directory: solver_application
      
      ```
