
# Классификация изображений дорожных знаков

## Описание проекта

Этот проект представляет собой решение задачи классификации изображений дорожных знаков с использованием сверточной нейронной сети (CNN) на базе TensorFlow/Keras. Основной целью является обучение модели, способной точно классифицировать изображения на основе предоставленных метаданных и изображений из набора данных.

## Структура проекта

```
project_root/
├── Ester_finalproject.ipynb         # Основной Jupyter Notebook
└── extracted_dataset/
    ├── Train.csv                    # Метаданные обучающей выборки
    ├── Test.csv                     # Метаданные тестовой выборки
    ├── Meta.csv                     # Описание классов
    ├── Train/                       # Каталог с обучающими изображениями
    └── Test/                        # Каталог с тестовыми изображениями
```

## Зависимости

Для запуска проекта необходимо установить следующие библиотеки:

```bash
pip install numpy pandas matplotlib opencv-python scikit-learn tensorflow
```

## Этапы работы

### 1. Импорт библиотек
Импортируются все необходимые библиотеки для загрузки, обработки изображений, визуализации и построения модели.

### 2. Загрузка данных
CSV-файлы загружаются с помощью `pandas`. Они содержат информацию о классах, именах файлов и других характеристиках изображений.

```python
train_df = pd.read_csv("extracted_dataset/Train.csv")
test_df = pd.read_csv("extracted_dataset/Test.csv")
meta_df = pd.read_csv("extracted_dataset/Meta.csv")
```

### 3. Первичный анализ данных
- Проверяется форма таблиц
- Подсчитывается количество уникальных классов
- Извлекается базовая информация из `Meta.csv`

### 4. Визуализация выборки
- Строятся графики распределения классов
- Отображаются примеры изображений каждого класса

### 5. Предобработка изображений
- Изменение размера изображений (например, до 32x32)
- Преобразование изображений в массивы numpy
- Нормализация значений пикселей
- Кодирование меток классов (one-hot encoding)

### 6. Разделение выборки
Данные разбиваются на обучающую и валидационную выборку с помощью `train_test_split`.

### 7. Аугментация данных
Используется `ImageDataGenerator` для увеличения обучающей выборки за счет:
- поворотов,
- масштабирования,
- сдвигов и пр.

### 8. Построение модели
Модель создается с использованием Sequential API Keras. Обычно она включает:
- Свёрточные слои (Conv2D)
- MaxPooling
- Dropout
- Полносвязные слои (Dense)

### 9. Компиляция и обучение
- Определяется функция потерь: `categorical_crossentropy`
- Оптимизатор: `adam`
- Метрика: `accuracy`
- Модель обучается на данных с валидацией по эпохам

### 10. Визуализация процесса обучения
Графики потерь и точности по эпохам:
- `train_loss`, `val_loss`
- `train_accuracy`, `val_accuracy`

### 11. Оценка модели
Выполняется оценка точности модели на тестовой выборке. Отображаются:
- Матрица ошибок
- Классы, которые путаются чаще всего

### 12. Предсказание и визуализация результатов
- Предсказываются метки для новых изображений
- Сопоставляются предсказания и реальные значения
- Визуализируются примеры правильных и ошибочных классификаций

## Запуск

1. Убедитесь, что все данные расположены в нужной директории.
2. Откройте `Ester_finalproject.ipynb` в Jupyter Notebook.
3. Последовательно выполните ячейки.
4. Проверьте пути к файлам, если работаете в другой системе.

## Примечания

- Убедитесь, что структура папок соответствует описанию.
- Возможна адаптация под Google Colab с учетом загрузки данных с Google Drive.
- Возможно дообучение модели или настройка гиперпараметров.

