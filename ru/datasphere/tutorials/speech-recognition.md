# Распознавание голоса

{{ ml-platform-full-name }} позволяет строить модели машинного обучения, используя интерфейс Jupyter Notebook. Познакомьтесь с решением задачи распознавания спикера по голосу с помощью моделирования речевых сигналов числовыми признаками:

1. [Установите зависимости](#satisfy-dependencies).
1. [Выполните загрузку данных и извлечение признаков](#load-dataset).
1. [Обучите модель на голосовых данных](#model-fit).
1. [Получите результаты предсказания признаков на тестовых данных](#model-test).

## Перед началом работы {#before-you-begin}

1. [Создайте проект](../operations/projects/create) в **{{ ml-platform-name }}** и откройте его.
1. [Склонируйте](../operations/projects/work-with-git.md#clone) Git-репозиторий, в котором находится подготовленный ноутбук с набором данных:

   ```
   https://github.com/donkrasnov/webinar0813_gbc_yandex
   ```

   Дождитесь, когда клонирование завершится, это может занять некоторое время. После завершения операции в блоке ![folder](../../_assets/datasphere/jupyterlab/folder.svg) **File Browser** появится каталог склонированного репозитория.

1. Откройте каталог **webinar0813_gbc_yandex** и ознакомьтесь с содержимым ноутбука **webinar-yandex-gbc.ipynb**. В начале ноутбука кратко изложены основные принципы моделирования речевого сигнала аудио-признаками.

   {% note info %}

   Если вы обновите вкладку браузера, на которой запущен ноутбук, или закроете ее, то состояние ноутбука сохранится. Переменные и результаты уже сделанных вычислений при этих действиях не сбрасываются.

   {% endnote %}

## Установите зависимости {#satisfy-dependencies}

1. Выделите все ячейки с кодом в разделе **Установка и импорт необходимых пакетов**, удерживая *Shift* и нажимая слева от нужных ячеек:

   ```
   %pip install numba==0.48.0
   %pip install librosa
   %pip install cffi==1.14.2
   %pip show numba
   import time
   import os
   from tqdm import tqdm
   ...
   ```

1. Запустите выделенные ячейки, выбрав в меню **Run → Run Selected Cells** (также можно использовать сочетание клавиш *Shift+Enter*).
1. Дождитесь завершения операции.

Часть пакетов уже установлена и импортируется с помощью команды `import`, часть устанавливается с помощью команды `%pip install` и затем импортируется. Полный список предустановленных в {{ ml-platform-name }} пакетов см. в разделе [{#T}](../concepts/preinstalled-packages.md).

## Загрузите набор данных из звуковых файлов {#load-dataset}

Перейдите к разделу **Генерация аудио-признаков**. В нем выполняются следующие операции:

1. Определяется функция для извлечения аудио-признаков из набора данных (используется [библиотека `librosa`](https://librosa.org/doc/latest/index.html)).
1. Загружается тестовый набор коротких десятисекундных аудио-фрагментов. С помощью этой функции извлекаются аудио-признаки. Так как данные распределены по папкам, относящимся к разным спикерам, можно однозначно сопоставить набору признаков конкретного спикера.
1. Полученный массив признаков нормируется.

Чтобы выполнить загрузку и обработку данных:

1. Выделите все ячейки с кодом в разделе **Генерация аудио-признаков** и запустите их.
1. Дождитесь завершения операции.

## Обучите модель на голосовых данных {#model-fit}

Перейдите к ячейке с кодом обучения моделей в разделе **Обучение моделей**. В данной ячейке в цикле по каждому спикеру выполняются следующие операции:

1. Модель обучается на фрагментах его речи.
1. Модуль `pickle` выполняет сохранение объекта обученной модели в файл в папке `./speaker-models`.

Чтобы обучить модель:

1. Добавьте `!#M` в начало ячейки для [изменения конфигурации ресурсов](../operations/projects/control-compute-resources.md), так как обучение модели — это ресурсоемкая операция:

   ```
   #!M

   start = time.time()

   features_smpl = pd.DataFrame()
   count = 1
   ...
   ```

1. Запустите ячейку.
1. Дождитесь завершения операции.

## Получите результаты предсказания признаков на тестовых данных {#model-test}

Перейдите к разделу **Тестирование на тестовом семпле**. В нем выполняются следующие операции:

1. Загружаются обученные модели из файлов `pickle`.
1. Выполняется загрузка и обработка аудио-файлов из тестового датасета подобно тому, как это делалось [для обучающего набора](#load-dataset).
1. Каждая модель предсказывает спикера по признакам.
1. Наилучший результат предсказания определяет выбор спикера.
1. Отображается точность определения выбранного в тесте спикера.

Чтобы получить результаты тестирования:

1. Выделите ячейку в разделе **Тестирование на тестовом семпле**.
1. Запустите ячейку.
1. Дождитесь завершения операции.
1. Убедитесь, что полученная точность определения спикера не менее 98%.

{% note info %}

Вы можете [поделиться](../operations/projects/publication.md) готовым ноутбуком с расчетами или [экспортировать проект](../operations/projects/export.md) целиком.

{% endnote %}