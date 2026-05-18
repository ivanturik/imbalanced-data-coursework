# Исследование методов обработки несбалансированных данных

Репозиторий содержит программную реализацию экспериментов для курсовой работы  
**«Исследование методов обработки несбалансированных данных в задачах бинарной классификации»**.

Основной файл проекта: `imbalanced-data.ipynb`.

---

## Быстрый запуск

### 1. Клонировать репозиторий

```bash
git clone https://github.com/ivanturik/imbalanced-data-coursework.git
cd imbalanced-data-coursework
```

### 2. Скачать датасеты

Архив с данными доступен в разделе **Releases**:

```text
https://github.com/ivanturik/imbalanced-data-coursework/releases/latest
```

Нужно скачать архив `data.zip` из релиза **All datasets** и распаковать его так, чтобы CSV-файлы оказались в папке `data/`.

Ожидаемая структура после распаковки:

```text
imbalanced-data-coursework/
├── data/
│   ├── creditcard.csv
│   ├── mammography.csv
│   ├── abalone19.csv
│   ├── AID362red_train.csv
│   └── AID362red_test.csv
├── imbalanced-data.ipynb
├── requirements.txt
└── README.md
```

### 3. Создать виртуальное окружение и установить зависимости

Для Windows:

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Если PowerShell запрещает активацию окружения, можно выполнить:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Затем снова:

```powershell
.venv\Scripts\Activate.ps1
```

Для Linux и macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 4. Запустить notebook

```bash
jupyter notebook imbalanced-data.ipynb
```

или:

```bash
jupyter lab imbalanced-data.ipynb
```

Для полного воспроизведения результатов рекомендуется выполнить все ячейки последовательно:

```text
Kernel → Restart Kernel and Run All Cells
```

---

## Состав репозитория

```text
.
├── imbalanced-data.ipynb        # основной notebook с экспериментами
├── requirements.txt             # список зависимостей Python
├── data/
│   └── .gitkeep                 # пустая папка для распаковки датасетов
├── results/
│   ├── figures/                 # графики, heatmap и матрицы ошибок
│   └── tables/                  # итоговые таблицы с результатами
├── .gitignore
└── README.md
```

---

## Описание проекта

Работа посвящена исследованию методов обработки несбалансированных данных в задачах бинарной классификации.

В задачах такого типа один класс представлен значительно большим числом объектов, чем другой. Из-за этого стандартные классификаторы могут смещаться в сторону класса большинства и плохо распознавать редкие, но важные объекты класса меньшинства.

В проекте сравниваются методы, которые позволяют уменьшить влияние дисбаланса классов и повысить качество классификации.

---

## Используемые данные

В работе используются два типа данных:

1. **Синтетические данные**, генерируемые внутри notebook.
2. **Реальные наборы данных**, скачиваемые отдельным архивом `data.zip` из раздела Releases.

Синтетические данные создаются с разными параметрами:

- отношение дисбаланса классов;
- уровень шума;
- степень перекрытия классов;
- размерность признакового пространства;
- размер выборки.

Реальные наборы данных:

- Credit Card Fraud Detection;
- Mammography;
- Abalone19;
- PubChem Bioassay AID362.

---

## Рассматриваемые методы

В проекте сравниваются несколько групп методов обработки дисбаланса.

### Методы уровня данных

- Random Oversampling;
- Random Undersampling;
- SMOTE;
- Borderline-SMOTE;
- ADASYN;
- SMOTE-ENN;
- SMOTE-Tomek.

### Методы уровня алгоритма

- Logistic Regression с `class_weight`;
- Random Forest с `class_weight`;
- cost-sensitive варианты моделей;
- собственная реализация взвешенной логистической регрессии.

### Ансамблевые методы

- Balanced Random Forest;
- Balanced Bagging;
- EasyEnsemble;
- RUSBoost.

### Настройка порога классификации

- стандартный порог `0.5`;
- подбор порога по F1-score;
- подбор порога по G-mean;
- GHOST-подход к выбору порога.

---

## Метрики качества

Для оценки качества моделей используются:

- Precision;
- Recall;
- F1-score;
- PR-AUC;
- ROC-AUC;
- G-mean;
- MCC;
- матрицы ошибок.

Использование нескольких метрик важно, потому что при сильном дисбалансе классов стандартная accuracy может давать завышенное представление о качестве модели.

---

## Результаты

Итоговые таблицы и графики сохраняются в папку `results/`.

Графики, heatmap и матрицы ошибок находятся в:

```text
results/figures/
```

Итоговые таблицы находятся в:

```text
results/tables/
```

---

## Воспроизводимость

Для воспроизводимости экспериментов в коде фиксируются значения `random_state` там, где это поддерживается используемыми алгоритмами.

При изменении версий библиотек, операционной системы или аппаратной платформы отдельные численные результаты могут незначительно отличаться.

---

## Основные зависимости

Проект использует следующие библиотеки Python:

- `numpy`;
- `pandas`;
- `scikit-learn`;
- `imbalanced-learn`;
- `matplotlib`;
- `seaborn`;
- `scipy`;
- `jupyter`.

Полный список зависимостей находится в файле `requirements.txt`.

---
Белорусский государственный университет  
Факультет прикладной математики и информатики  
2026
