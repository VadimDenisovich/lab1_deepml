# Лабораторная №1 — MLP и принятие купонов водителями

Основной результат: **lab1_coupon_mlp.ipynb**. Ячейки выполнены, результаты и графики сохранены внутри. Пояснения и ответы для защиты — на русском. Покрыты пункты 0–7 задания (суммарно 10 баллов по условию; оценку выставляет преподаватель).

## Запуск в подготовленном окружении

Из этой папки:

```bash
source .venv/bin/activate
python -m jupyterlab lab1_coupon_mlp.ipynb
```

Текущее `.venv` создано с `--system-site-packages`, чтобы использовать уже установленные библиотеки. Набор версий зафиксирован в `requirements.txt`. Это окружение не следует переносить на другой компьютер.

## Чистая установка на другом компьютере

Рекомендуется Python 3.13 (проверено на 3.13.7).

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m ipykernel install --sys-prefix --name lab1 --display-name "Python (lab1)"
python -m jupyterlab lab1_coupon_mlp.ipynb
```

Выберите ядро **Python (lab1)**, затем **Restart Kernel and Run All Cells**. Дождитесь окончания всех ячеек и сохраните ноутбук. Интернет нужен только для первоначальной установки пакетов. Обучение выполняется на CPU, 30 запусков с early stopping; время зависит от компьютера. Не перемещайте ноутбук отдельно от `data`.

## Файлы

- `lab1_coupon_mlp.ipynb` — весь код, анализ, исследования и пояснения.
- `data/in-vehicle-coupon-recommendation.csv` — оригинальные данные UCI.
- `results/` — история каждого запуска, таблицы метрик, PNG-графики, выводы, веса и обученная предобработка.
- `requirements.txt` — версии зависимостей.

Разбиение одно для всех моделей, примерно 70/15/15, с группировкой одинаковых входов. Предобработка обучается только на train. Выбор архитектуры — по среднему validation F1 трёх запусков. Финальный test оценивает базовую и выбранную модели с заранее фиксированным seed=42. Результаты test не используются для повторного подбора.

## Источник и лицензия

[UCI In-Vehicle Coupon Recommendation](https://archive.ics.uci.edu/dataset/603/in%2Bvehicle%2Bcoupon%2Brecommendation), DOI [10.24432/C5GS4P](https://doi.org/10.24432/C5GS4P), CC BY 4.0. Оригинальный CSV сохранён без изменений; очистка выполняется в ноутбуке. SHA256: `d47897367f5a12a31dece0f4e42d7bd9da76d7016b568da511b50335d08dcb43`.

Wang, Tong; Rudin, Cynthia; Doshi-Velez, Finale; Liu, Yimin; Klampfl, Erica; MacNeille, Perry. *A Bayesian framework for learning rule sets for interpretable classification*. JMLR 18 (2017), 2357–2393.

Данные отражают ответы опроса, а не реальные покупки; идентификаторов участников нет. В ноутбуке обсуждаются ограничения оценки.
