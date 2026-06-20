# Учебник по Processing

## Оглавление

1. [Введение в Processing](#1-введение-в-processing)
2. [Установка и настройка](#2-установка-и-настройка)
3. [Основы синтаксиса](#3-основы-синтаксиса)
4. [Переменные и типы данных](#4-переменные-и-типы-данных)
5. [Условные операторы](#5-условные-операторы)
6. [Циклы](#6-циклы)
7. [Функции](#7-функции)
8. [Массивы](#8-массивы)
9. [Система координат и трансформации](#9-система-координат-и-трансформации)
10. [Случайные числа](#10-случайные-числа)
11. [Анимация и время](#11-анимация-и-время)
12. [Работа с цветом](#12-работа-с-цветом)
13. [Обработка событий мыши и клавиатуры](#13-обработка-событий-мыши-и-клавиатуры)
14. [Текст и шрифты](#14-текст-и-шрифты)
15. [Создание оконных приложений](#15-создание-оконных-приложений)
16. [Классы и объекты (ООП)](#16-классы-и-объекты-ооп)
17. [Векторы и PVector](#17-векторы-и-pvector)
18. [Работа с изображениями](#18-работа-с-изображениями)
19. [Сохранение и загрузка данных](#19-сохранение-и-загрузка-данных)
20. [Основы Processing + Arduino](#20-основы-processing--arduino)
21. [Продвинутые проекты Processing + Arduino](#21-продвинутые-проекты-processing--arduino)
22. [Итоговый проект: Paint](#22-итоговый-проект-paint)
23. [Заключение](#23-заключение)

---

## 1. Введение в Processing

**Processing** — открытый язык программирования, основанный на Java. Представляет собой лёгкий и быстрый инструментарий для создания изображений, анимации и разработки интерфейсов.

Processing используется студентами, художниками, дизайнерами и исследователями для изучения программирования, прототипирования и создания визуальных проектов. Его главное преимущество — минимальный порог входа: вы можете нарисовать первую фигуру буквально в трёх строках кода.

### Зачем изучать Processing?

- **Визуальная обратная связь** — результат каждой команды виден сразу на экране.
- **Простой синтаксис** — основан на Java, но гораздо дружелюбнее к новичкам.
- **Широкие возможности** — от простых рисунков до сложной анимации и взаимодействия с внешними устройствами.
- **Активное сообщество** — тысячи примеров и библиотек.

### Связь с Arduino

Если вы уже знакомы с Arduino, то заметите много общего. Это не случайно: именно Processing послужил вдохновением для создателей Arduino. Среда разработки Arduino IDE построена на основе Processing IDE, а язык Wiring (на котором пишут для Arduino) основан на Processing.

Подробное руководство по подключению и совместной работе — в главах [20](#20-основы-processing--arduino) и [21](#21-продвинутые-проекты-processing--arduino) этого учебника.

<details>
<summary><b>Упражнения к разделу 1</b></summary>

1. **Вопрос.** Какие задачи можно решать с помощью Processing? Приведите три примера.
2. **Вопрос.** Чем Processing отличается от «обычных» языков программирования вроде Java или Python?
3. **Вопрос.** Почему Processing и Arduino так похожи?

</details>

---

## 2. Установка и настройка

На момент написания учебника актуальна версия Processing 4, поэтому мы будем использовать именно её.

### Шаг 1: Скачивание

- Перейдите на [официальный сайт Processing](https://processing.org/download/) и скачайте версию для вашей операционной системы.

### Шаг 2: Установка

- **Windows**: запустите установщик `.exe`.
- **macOS**: откройте `.dmg` и перетащите Processing в папку `Программы`.
- **Linux**: распакуйте архив и запустите файл `processing`.

### Шаг 3: Запуск

Запустите приложение. Перед вами откроется редактор с пустым файлом:

```
  [ Toolbar ]
  [ Text Editor ]  <- здесь пишем код
  [ Console ]      <- сюда выводятся сообщения
```

Среда разработки Processing минималистична: кнопки «Запустить» и «Стоп», редактор кода и консоль.

### Структура скетча

Скетч (программа на Processing) состоит минимум из двух функций:

- `setup()` — вызывается один раз при старте (настройки).
- `draw()` — вызывается в бесконечном цикле (рисование и анимация).

<details>
<summary><b>Упражнения к разделу 2</b></summary>

1. **Практика.** Скачайте и установите Processing. Создайте новый скетч и запустите его (пустой скетч должен показать серое окно).
2. **Практика.** Найдите в среде кнопки «Run» и «Stop». Напишите в консоли `println("Hello, Processing!");` внутри `setup()` и запустите.

</details>

---

## 3. Основы синтаксиса

### 3.1 Функция `setup()`

Функция `setup()` вызывается один раз при запуске программы. Здесь устанавливаются начальные параметры.

```java
void setup() {
  size(800, 600);    // Установка размера окна
  background(255);   // Установка белого фона
}
```

Команда `size(width, height)` задаёт размер окна. Если её не вызвать, окно будет размером 100×100.

### 3.2 Функция `draw()`

Функция `draw()` вызывается в цикле примерно 60 раз в секунду. Именно здесь происходит всё рисование и обновление экрана.

```java
void draw() {
  background(255);                         // Очистка фона
  fill(0);                                 // Установка чёрного цвета заливки
  ellipse(mouseX, mouseY, 50, 50);         // Рисование круга в позиции мыши
}
```

Если не вызывать `background()` внутри `draw()`, предыдущие рисунки останутся на экране — это можно использовать для создания «следов».

### 3.3 Рисование базовых фигур

Processing предоставляет простые команды для рисования форм:

| Команда                                | Описание                                     |
| -------------------------------------- | -------------------------------------------- |
| `line(x1, y1, x2, y2)`                 | Линия от точки (x1, y1) до (x2, y2)          |
| `rect(x, y, w, h)`                     | Прямоугольник с верхним левым углом в (x, y) |
| `ellipse(x, y, w, h)`                  | Эллипс с центром в (x, y)                    |
| `triangle(x1, y1, x2, y2, x3, y3)`     | Треугольник по трём вершинам                 |
| `point(x, y)`                          | Точка                                        |
| `quad(x1, y1, x2, y2, x3, y3, x4, y4)` | Четырёхугольник                              |
| `arc(x, y, w, h, start, stop)`         | Дуга                                         |

### Пример рисования

```java
void setup() {
  size(400, 400);
}

void draw() {
  background(255);

  fill(150, 0, 0);
  rect(50, 50, 100, 100);          // Красный квадрат

  fill(0, 150, 0);
  ellipse(200, 200, 100, 100);     // Зелёный круг

  fill(0, 0, 150);
  triangle(300, 50, 350, 150, 250, 150);  // Синий треугольник
}
```

### 3.4 Настройка обводки

Для управления обводкой фигур используются команды:

- `stroke(r, g, b)` — цвет линии/обводки.
- `strokeWeight(толщина)` — толщина линии.
- `noStroke()` — отключить обводку.

```java
void draw() {
  stroke(255, 0, 0);    // Красная обводка
  strokeWeight(5);      // Толщина 5 пикселей
  fill(200);
  rect(50, 50, 100, 100);
}
```

<details>
<summary><b>Упражнения к разделу 3</b></summary>

1. **Практика.** Нарисуйте домик: квадрат (стены), треугольник (крыша), прямоугольник (дверь) и два маленьких квадрата (окна).
2. **Практика.** Нарисуйте светофор: три круга (красный, жёлтый, зелёный) друг под другом в прямоугольнике.
3. **Практика.** Используя `line()`, нарисуйте звезду (пятиконечную) в центре экрана.

</details>

---

## 4. Переменные и типы данных

Переменные хранят значения, которые могут меняться во время работы программы.

### 4.1 Типы данных

Processing поддерживает те же типы, что и Java:

| Тип       | Описание                         | Пример                        |
| --------- | -------------------------------- | ----------------------------- |
| `int`     | Целое число                      | `int x = 10;`                 |
| `float`   | Число с плавающей точкой         | `float pi = 3.14;`            |
| `boolean` | Логическое значение (true/false) | `boolean flag = true;`        |
| `char`    | Один символ                      | `char letter = 'A';`          |
| `String`  | Строка текста                    | `String name = "Processing";` |
| `color`   | Цвет                             | `color c = color(255, 0, 0);` |

### 4.2 Объявление и инициализация

```java
void setup() {
  int x = 100;               // Объявление + инициализация
  float y;                   // Только объявление
  y = 200.5;                 // Инициализация позже

  String greeting = "Привет!";
  println(greeting + " x = " + x);
}
```

### 4.3 Встроенные системные переменные

Processing предоставляет готовые переменные:

- `width`, `height` — ширина и высота окна.
- `mouseX`, `mouseY` — текущие координаты мыши.
- `pmouseX`, `pmouseY` — предыдущие координаты мыши.
- `frameCount` — количество прошедших кадров.
- `frameRate` — частота кадров (кадров/сек).

### 4.4 Область видимости (scope)

Переменные, объявленные вне функций, видны во всём скетче (глобальные). Переменные внутри функции видны только в ней.

```java
int globalX = 200;  // Глобальная переменная

void setup() {
  int localY = 50;  // Локальная переменная
  println(globalX); // ✅ Доступна
  println(localY);  // ✅ Доступна
}

void draw() {
  println(globalX); // ✅ Доступна
  println(localY);  // ❌ Ошибка! localY не видна здесь
}
```

### 4.5 Математические операции

```java
int a = 10 + 5;    // Сложение
int b = 10 - 5;    // Вычитание
int c = 10 * 5;    // Умножение
int d = 10 / 5;    // Деление (целочисленное для int)
float e = 10.0 / 3.0; // Деление (вещественное)
int f = 10 % 3;    // Остаток от деления (1)
```

Полезные встроенные функции:

- `map(value, fromLow, fromHigh, toLow, toHigh)` — переводит число из одного диапазона в другой.
- `constrain(value, min, max)` — ограничивает значение диапазоном.
- `dist(x1, y1, x2, y2)` — расстояние между двумя точками.
- `lerp(a, b, t)` — линейная интерполяция.

<details>
<summary><b>Упражнения к разделу 4</b></summary>

1. **Практика.** Объявите переменные для x и y круга. Заставьте круг двигаться по диагонали, увеличивая x и y на 1 каждый кадр.
2. **Практика.** Используя `map()`, сделайте так, чтобы круг следовал за мышью по X, но с отображением диапазона 0–width в диапазон 0–255 (цвет).
3. **Практика.** Нарисуйте две точки и выведите на экран расстояние между ними, используя `dist()`.

</details>

---

## 5. Условные операторы

Условные операторы позволяют выполнять код в зависимости от выполнения условий.

### 5.1 `if`, `else if`, `else`

```java
void draw() {
  background(255);

  if (mouseX < width / 3) {
    fill(255, 0, 0);        // Красный, если мышь в левой трети
  } else if (mouseX < 2 * width / 3) {
    fill(0, 255, 0);        // Зелёный, если мышь в центре
  } else {
    fill(0, 0, 255);        // Синий, если мышь в правой трети
  }

  ellipse(mouseX, height / 2, 100, 100);
}
```

### 5.2 Логические операторы

- `&&` — логическое И (оба условия истинны)
- `||` — логическое ИЛИ (хотя бы одно истинно)
- `!` — логическое НЕ (отрицание)

```java
// Круг зелёный только если мышь в квадрате 200×200 в центре
if (mouseX > 100 && mouseX < 300 && mouseY > 100 && mouseY < 300) {
  fill(0, 255, 0);
} else {
  fill(255, 0, 0);
}
ellipse(width / 2, height / 2, 100, 100);
```

### 5.3 Операторы сравнения

| Оператор | Значение         |
| -------- | ---------------- |
| `==`     | Равно            |
| `!=`     | Не равно         |
| `<`      | Меньше           |
| `>`      | Больше           |
| `<=`     | Меньше или равно |
| `>=`     | Больше или равно |

<details>
<summary><b>Упражнения к разделу 5</b></summary>

1. **Практика.** Нарисуйте квадрат, который меняет цвет при наведении мыши (проверяйте попадание курсора внутрь квадрата).
2. **Практика.** Сделайте программу, которая выводит «Утро», «День», «Вечер» или «Ночь» в зависимости от значения `hour()`.
3. **Практика.** Нарисуйте «тепловую карту»: цвет фона плавно меняется от синего к красному в зависимости от расстояния от мыши до центра экрана. Используйте `dist()` и `map()`.

</details>

---

## 6. Циклы

Циклы позволяют повторять действия многократно без дублирования кода.

### 6.1 `for`

Используется, когда известно количество повторений.

```java
void draw() {
  background(255);

  // Рисуем 10 кругов по горизонтали
  for (int i = 0; i < 10; i++) {
    float x = map(i, 0, 9, 50, width - 50);
    ellipse(x, height / 2, 40, 40);
  }
}
```

### 6.2 `while`

Используется, когда количество повторений заранее неизвестно.

```java
void draw() {
  background(255);
  int i = 0;
  while (i < 10) {
    float x = map(i, 0, 9, 50, width - 50);
    ellipse(x, height / 2, 40, 40);
    i++;
  }
}
```

### 6.3 Вложенные циклы

Очень полезны для создания сеток и таблиц.

```java
void draw() {
  background(255);

  for (int row = 0; row < 5; row++) {
    for (int col = 0; col < 8; col++) {
      float x = map(col, 0, 7, 40, width - 40);
      float y = map(row, 0, 4, 40, height - 40);
      fill(col * 30, row * 50, 150);
      rect(x, y, 30, 30);
    }
  }
}
```

<details>
<summary><b>Упражнения к разделу 6</b></summary>

1. **Практика.** Используя цикл `for`, нарисуйте линейку с делениями от 0 до 100 по горизонтали (каждое деление — линия высотой 10 пикселей, каждое десятое — 20 пикселей).
2. **Практика.** Вложенными циклами нарисуйте шахматную доску 8×8 (чередование чёрных и белых квадратов).
3. **Практика.** Нарисуйте 100 кругов со случайными координатами и размерами (используйте `random()` внутри цикла).

</details>

---

## 7. Функции

Функции помогают организовать код и избежать повторений.

### 7.1 Создание своей функции

```java
void setup() {
  size(400, 400);
}

void draw() {
  background(255);
  drawFlower(100, 100, 30);
  drawFlower(300, 200, 50);
  drawFlower(200, 300, 40);
}

// Своя функция: рисует цветок в позиции (x, y)
void drawFlower(float x, float y, float size) {
  fill(255, 255, 0);
  ellipse(x, y, size, size);           // Центр

  fill(255, 100, 100);
  for (int i = 0; i < 5; i++) {
    float angle = TWO_PI / 5 * i;
    float px = x + cos(angle) * size;
    float py = y + sin(angle) * size;
    ellipse(px, py, size * 0.6, size * 0.6);  // Лепестки
  }
}
```

### 7.2 Функции с возвращаемым значением

Функция может не только выполнять действия, но и возвращать результат.

```java
void draw() {
  background(255);
  float speed = calculateSpeed(mouseX, mouseY);
  ellipse(mouseX, mouseY, 20 + speed, 20 + speed);
}

float calculateSpeed(float x, float y) {
  float centerDist = dist(x, y, width / 2, height / 2);
  return map(centerDist, 0, width / 2, 1, 10);
}
```

### 7.3 Параметры по умолчанию (перегрузка функций)

В Java/Processing можно создавать несколько функций с одинаковым именем, но разными параметрами.

```java
void setup() {
  setColor();          // Установит цвет по умолчанию
  setColor(255, 0, 0); // Установит красный
}

void setColor() {
  fill(128);
}

void setColor(int r, int g, int b) {
  fill(r, g, b);
}
```

<details>
<summary><b>Упражнения к разделу 7</b></summary>

1. **Практика.** Напишите функцию `drawHouse(x, y, size)`, которая рисует домик. Вызовите её несколько раз в разных местах экрана с разными размерами.
2. **Практика.** Напишите функцию `float temperatureToColor(float temp)`, которая принимает температуру (0–100) и возвращает цвет от синего (0) до красного (100). Используйте `map()` и `lerpColor()`.

</details>

---

## 8. Массивы

Массивы позволяют хранить множество значений одного типа под одним именем.

### 8.1 Создание и заполнение

```java
int[] numbers = new int[5];          // Массив из 5 элементов
numbers[0] = 10;
numbers[1] = 20;
numbers[2] = 30;
numbers[3] = 40;
numbers[4] = 50;

// Короткая запись
int[] values = { 10, 20, 30, 40, 50 };

float[] randoms = new float[100];
for (int i = 0; i < randoms.length; i++) {
  randoms[i] = random(255);
}
```

### 8.2 Использование массива в анимации

Массивы идеально подходят для хранения множества объектов (частиц, точек, шариков).

```java
float[] x = new float[50];
float[] y = new float[50];
float[] speeds = new float[50];

void setup() {
  size(600, 400);
  for (int i = 0; i < x.length; i++) {
    x[i] = random(width);
    y[i] = random(height);
    speeds[i] = random(1, 5);
  }
}

void draw() {
  background(255);
  for (int i = 0; i < x.length; i++) {
    y[i] += speeds[i];
    if (y[i] > height) y[i] = 0;
    ellipse(x[i], y[i], 10, 10);
  }
}
```

### 8.3 Двумерные массивы

```java
int[][] grid = new int[8][8];

void setup() {
  size(400, 400);
  for (int i = 0; i < 8; i++) {
    for (int j = 0; j < 8; j++) {
      grid[i][j] = (i + j) % 2 == 0 ? 255 : 0;
    }
  }
}

void draw() {
  for (int i = 0; i < 8; i++) {
    for (int j = 0; j < 8; j++) {
      fill(grid[i][j]);
      rect(i * 50, j * 50, 50, 50);
    }
  }
}
```

### 8.4 ArrayList — динамический массив

Когда количество элементов заранее неизвестно, удобнее использовать `ArrayList`.

```java
import java.util.ArrayList;

ArrayList<Float> values = new ArrayList<Float>();

void draw() {
  values.add(mouseX);
  if (values.size() > 100) {
    values.remove(0);
  }

  background(255);
  for (int i = 0; i < values.size(); i++) {
    ellipse(values.get(i), height / 2, 5, 5);
  }
}
```

<details>
<summary><b>Упражнения к разделу 8</b></summary>

1. **Практика.** Создайте массив из 20 «снежинок» (кружков), которые падают сверху вниз с разными скоростями. Когда снежинка достигает низа, она появляется наверху.
2. **Практика.** Используя двумерный массив, создайте игру «Жизнь» Конвея или просто нарисуйте шахматную доску, где клетки перекрашиваются случайным образом каждые 30 кадров.

</details>

---

## 9. Система координат и трансформации

### 9.1 Система координат

В Processing начало координат (0, 0) находится в **верхнем левом** углу. Ось X направлена вправо, ось Y — вниз.

```
(0,0) ──────────► X
  │
  │
  ▼
  Y
```

### 9.2 `pushMatrix()` и `popMatrix()`

Эти команды сохраняют и восстанавливают текущую систему координат. Они позволяют временно перемещать, вращать и масштабировать отдельные объекты, не влияя на остальной рисунок.

### 9.3 `translate()`, `rotate()`, `scale()`

```java
void draw() {
  background(255);

  // Рисуем квадрат без трансформации
  fill(200);
  rect(0, 0, 50, 50);

  pushMatrix();
  translate(100, 100);     // Сдвигаем начало координат
  rotate(radians(45));     // Поворачиваем на 45 градусов
  scale(1.5);              // Увеличиваем в 1.5 раза
  fill(255, 0, 0);
  rect(0, 0, 50, 50);      // Рисуем в новой системе координат
  popMatrix();

  // Этот квадрат не зависит от трансформаций выше
  fill(0, 255, 0);
  rect(100, 200, 50, 50);
}
```

### 9.4 Анимация вращения

```java
float angle = 0;

void draw() {
  background(255);

  pushMatrix();
  translate(width / 2, height / 2);
  rotate(angle);
  rectMode(CENTER);
  fill(100, 150, 255);
  rect(0, 0, 100, 100);
  popMatrix();

  angle += 0.02;
}
```

<details>
<summary><b>Упражнения к разделу 9</b></summary>

1. **Практика.** Используя `pushMatrix()` / `popMatrix()` и `rotate()`, создайте анимированные часы со стрелками (часовая, минутная, секундная).
2. **Практика.** Нарисуйте «снежинку» из 6 лучей, используя `rotate()` и цикл внутри `pushMatrix()` / `popMatrix()`.

</details>

---

## 10. Случайные числа

### 10.1 `random()`

Функция `random()` возвращает случайное число.

```java
float r = random(100);          // Случайное число от 0 до 100
float r2 = random(50, 100);     // Случайное число от 50 до 100
int r3 = (int) random(10);      // Случайное целое от 0 до 9
```

### 10.2 Пример: случайные круги

```java
void setup() {
  size(600, 400);
  background(255);
  noLoop();  // Остановить draw() после первого кадра
}

void draw() {
  for (int i = 0; i < 100; i++) {
    float x = random(width);
    float y = random(height);
    float r = random(10, 50);
    fill(random(255), random(255), random(255), random(100, 200));
    noStroke();
    ellipse(x, y, r, r);
  }
}
```

### 10.3 Функция `noise()`

Для более естественных, плавных случайных значений используется шум Перлина:

```java
void setup() {
  size(400, 400);
}

void draw() {
  float n = noise(frameCount * 0.01);  // Плавное случайное значение от 0 до 1
  float x = map(n, 0, 1, 0, width);
  ellipse(x, height / 2, 20, 20);
}
```

<details>
<summary><b>Упражнения к разделу 10</b></summary>

1. **Практика.** Создайте программу, которая в случайных местах экрана рисует разноцветные круги случайного размера. При нажатии на пробел экран очищается.
2. **Практика.** Используя шум Перлина `noise()`, создайте плавно движущуюся точку, которая имитирует полёт мухи.

</details>

---

## 11. Анимация и время

### 11.1 `frameCount`

Счётчик кадров — увеличивается на 1 каждый вызов `draw()`.

```java
void draw() {
  background(255);
  float x = (frameCount * 2) % width;  // Движение слева направо
  ellipse(x, height / 2, 30, 30);
}
```

### 11.2 `millis()`

Возвращает количество миллисекунд, прошедших с запуска.

```java
void draw() {
  background(255);

  float t = millis() / 1000.0;  // Время в секундах
  float x = map(sin(t), -1, 1, 50, width - 50);

  fill(255, 0, 0);
  ellipse(x, height / 2, 40, 40);

  fill(0);
  text("Время: " + nf(t, 0, 1) + " сек", 20, 30);
}
```

### 11.3 Sin и Cos для плавных движений

```java
float angle = 0;

void draw() {
  background(255);

  // Плавное движение по кругу
  float x = width / 2 + cos(angle) * 150;
  float y = height / 2 + sin(angle) * 150;

  fill(100, 150, 255);
  ellipse(x, y, 40, 40);

  angle += 0.02;
}
```

<details>
<summary><b>Упражнения к разделу 11</b></summary>

1. **Практика.** Сделайте анимацию: шарик отскакивает от стенок. Используйте переменные `speedX`, `speedY` и проверку границ.
2. **Практика.** Используя `sin()`, создайте анимацию, где круг плавно изменяет размер (пульсирует) и цвет от красного к синему.

</details>

---

## 12. Работа с цветом

### 12.1 Цветовые модели

Processing поддерживает несколько цветовых моделей. По умолчанию используется **RGB** (Red, Green, Blue) со значениями от 0 до 255.

```java
fill(255, 0, 0);       // Красный (R=255, G=0, B=0)
fill(0, 255, 0);       // Зелёный
fill(0, 0, 255);       // Синий
fill(255, 255, 0);     // Жёлтый
fill(128, 128, 128);   // Серый
```

### 12.2 Прозрачность (альфа-канал)

Четвёртый параметр задаёт прозрачность (0 — полностью прозрачный, 255 — полностью непрозрачный):

```java
fill(255, 0, 0, 100);   // Полупрозрачный красный
fill(0, 0, 255, 50);    // Очень прозрачный синий
```

### 12.3 `colorMode()`

Можно переключиться в режим HSB (Hue, Saturation, Brightness):

```java
void setup() {
  size(400, 400);
  colorMode(HSB, 360, 100, 100);  // H: 0-360, S: 0-100, B: 0-100
}

void draw() {
  background(200);
  for (int i = 0; i < 360; i += 10) {
    fill(i, 80, 100);
    rect(i * (width / 360.0), 0, width / 36.0, height);
  }
}
```

### 12.4 `lerpColor()`

Плавный переход между двумя цветами:

```java
color c1 = color(255, 0, 0);
color c2 = color(0, 0, 255);

void draw() {
  float t = map(mouseX, 0, width, 0, 1);
  color current = lerpColor(c1, c2, t);
  background(current);

  fill(0);
  text("Смешение: " + nf(t, 0, 2), 20, 30);
}
```

<details>
<summary><b>Упражнения к разделу 12</b></summary>

1. **Практика.** Нарисуйте несколько кругов, частично перекрывающих друг друга, каждый со своей прозрачностью. Посмотрите, как цвета смешиваются.

</details>

---

## 13. Обработка событий мыши и клавиатуры

### 13.1 Мышь

Processing предоставляет несколько встроенных функций и переменных для работы с мышью.

```java
void setup() {
  size(400, 400);
}

void draw() {
  background(255);
  ellipse(mouseX, mouseY, 30, 30);
}

void mousePressed() {
  println("Мышь нажата в (" + mouseX + ", " + mouseY + ")");
}

void mouseReleased() {
  println("Мышь отпущена");
}

void mouseClicked() {
  println("Клик!");
}

void mouseDragged() {
  println("Перетаскивание...");
}

void mouseMoved() {
  println("Движение мыши");
}

void mouseWheel(MouseEvent event) {
  float delta = event.getCount();
  println("Колесико: " + delta);
}
```

### 13.2 Клавиатура

```java
void setup() {
  size(400, 400);
}

void draw() {
  // Рисование зависит от нажатой клавиши
  if (keyPressed) {
    fill(255, 0, 0);
    text("Нажата: " + key, 20, 30);
  }
}

void keyPressed() {
  println("Клавиша нажата: " + key + " (код: " + keyCode + ")");

  if (key == 'r') {
    background(255, 0, 0);
  } else if (key == 'g') {
    background(0, 255, 0);
  } else if (key == 'b') {
    background(0, 0, 255);
  } else if (keyCode == UP) {
    println("Стрелка вверх!");
  }
}

void keyReleased() {
  println("Клавиша отпущена");
}
```

### 13.3 Практический пример: клавиатурный Paint

```java
float brushSize = 10;
color brushColor = color(0);

void setup() {
  size(600, 400);
  background(255);
}

void draw() {
  if (mousePressed) {
    stroke(brushColor);
    strokeWeight(brushSize);
    line(mouseX, mouseY, pmouseX, pmouseY);
  }
}

void keyPressed() {
  if (key == '1') brushColor = color(255, 0, 0);
  if (key == '2') brushColor = color(0, 255, 0);
  if (key == '3') brushColor = color(0, 0, 255);
  if (key == '+') brushSize += 2;
  if (key == '-') brushSize = max(1, brushSize - 2);
  if (key == ' ') background(255);  // Очистка
}
```

<details>
<summary><b>Упражнения к разделу 13</b></summary>

1. **Практика.** Сделайте программу, где кружок двигается стрелками клавиатуры (UP, DOWN, LEFT, RIGHT).
2. **Практика.** Сделайте программу «Крестики-нолики» с рисованием по клику мыши. (Достаточно просто ставить X и O в клетки по очереди.)

</details>

---

## 14. Текст и шрифты

Работа с текстом — важная часть любого приложения. Processing предоставляет гибкие инструменты для вывода и форматирования текста.

### 14.1 Вывод текста: `text()`

Базовый вывод текста осуществляется функцией `text()`:

```java
void setup() {
  size(400, 200);
  background(255);
}

void draw() {
  background(255);
  fill(0);
  text("Привет, Processing!", 20, 100);
}
```

Функция `text()` принимает строку и координаты (x, y), где **y** — это базовая линия (baseline) текста.

### 14.2 Размер и настройки текста

- `textSize(size)` — задаёт размер шрифта в пикселях.
- `textLeading(value)` — межстрочный интервал.
- `textMode(MODEL)` или `textMode(SHAPE)` — режим отрисовки.

```java
void draw() {
  background(255);
  textSize(16);
  text("Маленький текст", 20, 50);

  textSize(32);
  text("Средний текст", 20, 100);

  textSize(48);
  fill(100, 100, 255);
  text("Крупный текст", 20, 160);
}
```

### 14.3 Выравнивание текста: `textAlign()`

```java
void draw() {
  background(255);
  stroke(200);
  line(width / 2, 0, width / 2, height);

  textSize(20);

  textAlign(LEFT);
  text("LEFT", width / 2, 40);

  textAlign(CENTER);
  text("CENTER", width / 2, 80);

  textAlign(RIGHT);
  text("RIGHT", width / 2, 120);

  textAlign(CENTER, TOP);
  text("TOP", width / 2, 160);

  textAlign(CENTER, CENTER);
  text("CENTER", width / 2, 200);

  textAlign(CENTER, BOTTOM);
  text("BOTTOM", width / 2, 240);
}
```

### 14.4 Ширина и высота текста

- `textWidth(string)` — возвращает ширину строки в пикселях.
- `textAscent()` — высота символов над baseline.
- `textDescent()` — высота символов под baseline.

```java
void draw() {
  background(255);
  textSize(24);

  String msg = "Processing";
  float tw = textWidth(msg);

  fill(200, 200, 255);
  rect(20, 50, tw, textAscent() + textDescent());

  fill(0);
  text(msg, 20, 50 + textAscent());

  fill(255, 200, 200);
  float boxX = 200, boxY = 150, boxW = 150, boxH = 40;
  rect(boxX, boxY, boxW, boxH);

  fill(0);
  textAlign(CENTER, CENTER);
  textSize(16);
  text("Центр", boxX + boxW / 2, boxY + boxH / 2);
}
```

### 14.5 Работа со шрифтами

Processing по умолчанию использует шрифт sans-serif. Для загрузки своих шрифтов:

```java
PFont myFont;

void setup() {
  size(400, 200);
  myFont = createFont("Arial", 24);
  textFont(myFont);
}

void draw() {
  background(255);
  fill(0);
  text("Текст с Arial", 20, 100);
}
```

Чтобы использовать шрифт из файла `.ttf`, поместите его в папку `data` скетча и загрузите: `createFont("Minecraftia.ttf", 24)`.

Просмотр доступных шрифтов:

```java
void setup() {
  String[] fonts = PFont.list();
  println(fonts);
}
```

### 14.6 Форматирование чисел

| Функция       | Описание                            | Пример                       |
| ------------- | ----------------------------------- | ---------------------------- |
| `nf(n, d, p)`  | Число с фиксированным кол-вом цифр | `nf(3.14, 2, 1)` → `"03.1"` |
| `nfc(n, p)`    | Число с разделителями разрядов      | `nfc(12345, 2)` → `"12,345.00"` |
| `nfp(n, d, p)` | Число со знаком `+`                 | `nfp(5, 2, 0)` → `"+05"`    |
| `nfs(n, d, p)` | Число с пробелом перед полож.      | `nfs(5, 2, 0)` → `" 05"`    |

```java
void draw() {
  background(255);
  textSize(16);

  float val = mouseX * 0.1;

  text("raw:     " + val, 20, 40);
  text("nf:      " + nf(val, 3, 2), 20, 70);
  text("nfc:     " + nfc(val, 2), 20, 100);
  text("nfp:     " + nfp(val, 3, 2), 20, 130);
}
```

### 14.7 Многострочный текст

Processing поддерживает автоматический перенос слов, если указать ширину области:

```java
void draw() {
  background(255);
  fill(0);
  textSize(16);

  String t = "Это длинный текст, который будет автоматически разбит на несколько строк, если указать ширину области.";
  text(t, 20, 40, 300, 200);  // bounding box: ширина 300, высота 200
}
```

Четвёртый и пятый параметры `text()` задают ширину и высоту области.

### 14.8 Стили шрифта

```java
void draw() {
  background(255);

  PFont boldFont = createFont("Arial-Bold", 20);
  textFont(boldFont);
  fill(0);
  text("Жирный текст", 20, 50);

  PFont italicFont = createFont("Arial-Italic", 20);
  textFont(italicFont);
  text("Курсивный текст", 20, 100);

  PFont boldItalicFont = createFont("Arial-BoldItalic", 20);
  textFont(boldItalicFont);
  text("Жирный курсив", 20, 150);
}
```

<details>
<summary><b>Упражнения к разделу 14</b></summary>

1. **Практика.** Напишите программу «Счётчик кликов»: при каждом клике мыши число на экране увеличивается. Используйте `textAlign(CENTER, CENTER)`, чтобы текст был по центру.
2. **Практика.** Выведите координаты мыши в формате `X: 0420, Y: 0300` (всегда 4 цифры, используйте `nf()`).
3. **Практика.** Напишите программу, которая выводит случайную цитату из массива строк при нажатии пробела. Текст должен автоматически переноситься.

</details>

---

## 15. Создание оконных приложений

Processing позволяет не только рисовать графику, но и создавать полноценные оконные приложения с элементами интерфейса.

### 15.1 Управление окном через `surface`

Объект `surface` предоставляет доступ к свойствам окна:

```java
void setup() {
  size(400, 300);

  surface.setTitle("Моё приложение");
  surface.setResizable(true);
  surface.setLocation(100, 100);
}

void draw() {
  background(255);
  fill(0);
  text("Размер окна: " + width + "×" + height, 20, 40);
}
```

### 15.2 Полный экран и режимы

```java
void setup() {
  fullScreen();                         // Полный экран
  // fullScreen(1);                     // Второй монитор
  // fullScreen(P2D);                   // 2D-рендерер

  surface.setTitle("Fullscreen App");
}

void draw() {
  background(0);
  fill(255);
  textSize(32);
  textAlign(CENTER, CENTER);
  text("Fullscreen Mode", width / 2, height / 2);
  textSize(16);
  text("Нажми ESC для выхода", width / 2, height / 2 + 40);
}
```

- `windowMove(x, y)` — переместить окно.
- `windowResizable(true/false)` — разрешить/запретить изменение размера.
- `noSmooth()` — отключить сглаживание (для пиксель-арта).

### 15.3 Создание кнопок (без библиотек)

```java
boolean button1Pressed = false;
boolean button2Pressed = false;

void setup() {
  size(400, 300);
  surface.setTitle("Кнопки");
}

void draw() {
  background(240);

  drawButton(50, 100, 120, 50, "Кнопка 1", button1Pressed);
  drawButton(230, 100, 120, 50, "Кнопка 2", button2Pressed);

  fill(0);
  textSize(16);
  text("Кнопка 1: " + (button1Pressed ? "ВКЛ" : "ВЫКЛ"), 50, 240);
  text("Кнопка 2: " + (button2Pressed ? "ВКЛ" : "ВЫКЛ"), 50, 270);
}

void drawButton(int x, int y, int w, int h, String label, boolean pressed) {
  if (pressed) {
    fill(150, 200, 255);
    stroke(100, 150, 200);
  } else {
    fill(220);
    stroke(180);
  }
  strokeWeight(2);
  rect(x, y, w, h, 5);

  fill(pressed ? 0 : 50);
  textAlign(CENTER, CENTER);
  textSize(16);
  text(label, x + w / 2, y + h / 2);
}

void mousePressed() {
  if (isInside(mouseX, mouseY, 50, 100, 120, 50)) {
    button1Pressed = !button1Pressed;
  }
  if (isInside(mouseX, mouseY, 230, 100, 120, 50)) {
    button2Pressed = !button2Pressed;
  }
}

boolean isInside(int mx, int my, int x, int y, int w, int h) {
  return mx > x && mx < x + w && my > y && my < y + h;
}
```

### 15.4 Создание слайдера (без библиотек)

```java
int sliderX = 300;
int sliderMin = 50, sliderMax = 350;
boolean dragging = false;

void setup() {
  size(400, 200);
  surface.setTitle("Слайдер");
}

void draw() {
  background(240);

  fill(200);
  rect(50, 80, 300, 10, 5);

  fill(100, 150, 255);
  ellipse(sliderX, 85, 20, 20);

  float val = map(sliderX, sliderMin, sliderMax, 0, 100);
  fill(0);
  textAlign(CENTER, CENTER);
  textSize(20);
  text(nf(val, 0, 1) + "%", width / 2, 150);
}

void mousePressed() {
  if (dist(mouseX, mouseY, sliderX, 85) < 15) {
    dragging = true;
  }
}

void mouseDragged() {
  if (dragging) {
    sliderX = constrain(mouseX, sliderMin, sliderMax);
  }
}

void mouseReleased() {
  dragging = false;
}
```

### 15.5 Чекбоксы

```java
boolean optionA = true;
boolean optionB = false;
boolean optionC = false;

void setup() {
  size(300, 250);
}

void draw() {
  background(240);

  textSize(16);
  fill(0);
  text("Выберите опции:", 20, 30);

  drawCheckbox(20, 60, 16, optionA, "Вариант A");
  drawCheckbox(20, 100, 16, optionB, "Вариант B");
  drawCheckbox(20, 140, 16, optionC, "Вариант C");

  fill(0);
  String selected = "";
  if (optionA) selected += "A ";
  if (optionB) selected += "B ";
  if (optionC) selected += "C ";
  text("Выбрано: " + selected, 20, 200);
}

void drawCheckbox(int x, int y, int s, boolean checked, String label) {
  stroke(150);
  strokeWeight(1);
  fill(checked ? color(100, 150, 255) : 255);
  rect(x, y, s, s);

  if (checked) {
    stroke(255);
    strokeWeight(2);
    line(x + 3, y + 3, x + s - 3, y + s - 3);
    line(x + s - 3, y + 3, x + 3, y + s - 3);
  }

  fill(0);
  textAlign(LEFT, CENTER);
  textSize(14);
  text(label, x + s + 10, y + s / 2);
}

void mousePressed() {
  if (isInside(mouseX, mouseY, 20, 60, 16, 16)) optionA = !optionA;
  if (isInside(mouseX, mouseY, 20, 100, 16, 16)) optionB = !optionB;
  if (isInside(mouseX, mouseY, 20, 140, 16, 16)) optionC = !optionC;
}

boolean isInside(int mx, int my, int x, int y, int w, int h) {
  return mx > x && mx < x + w && my > y && my < y + h;
}
```

### 15.6 Библиотека ControlP5

Для серьёзных GUI-проектов установите библиотеку: `Скетч → Импорт библиотеки → ControlP5`.

```java
import controlP5.*;

ControlP5 cp5;

void setup() {
  size(400, 400);
  cp5 = new ControlP5(this);

  cp5.addButton("clickMe")
    .setPosition(50, 50)
    .setSize(100, 40)
    .setCaptionLabel("Нажми меня");

  cp5.addSlider("brightness")
    .setPosition(50, 120)
    .setSize(300, 20)
    .setRange(0, 255)
    .setValue(128);

  cp5.addList("shapeList")
    .setPosition(50, 170)
    .setSize(200, 100)
    .setOpen(false)
    .addItem("Круг", 0)
    .addItem("Квадрат", 1)
    .addItem("Треугольник", 2);
}

void draw() {
  background(220);
}

void clickMe() {
  println("Кнопка нажата!");
}

void brightness(int val) {
  background(val);
}

void shapeList(int val) {
  println("Выбран элемент: " + val);
}
```

### 15.7 Иконка окна

```java
void setup() {
  size(400, 300);

  PImage icon = loadImage("icon.png");
  surface.setIcon(icon);
  surface.setTitle("Приложение с иконкой");
}

void draw() {
  background(255);
}
```

<details>
<summary><b>Упражнения к разделу 15</b></summary>

1. **Практика.** Создайте приложение с тремя кнопками: «Красный», «Зелёный», «Синий». При нажатии фон окна меняется на соответствующий цвет. Добавьте заголовок окна «Цветовой переключатель».
2. **Практика.** Сделайте конвертер температуры: слайдер для ввода °C (0–100), рядом — значение в °F. Используйте ручное рисование слайдера (без ControlP5).
3. **Практика.** Создайте простое TODO-приложение: поле для ввода текста, кнопка «Добавить», список задач на экране.

</details>

---

## 16. Классы и объекты (ООП)

В Processing можно создавать свои типы данных — **классы**. Это основа объектно-ориентированного программирования (ООП), которая позволяет группировать данные и функции в одну сущность — **объект**.

### 16.1 Что такое класс?

**Класс** — это шаблон (чертёж), описывающий состояние (поля) и поведение (методы) объектов.

**Объект** — конкретный экземпляр класса.

### 16.2 Создание класса

```java
class Ball {
  float x, y;     // Поля (данные)
  float vx, vy;
  float r;

  // Конструктор — вызывается при создании объекта
  Ball(float x, float y) {
    this.x = x;
    this.y = y;
    this.r = 20;
    this.vx = random(-2, 2);
    this.vy = random(-2, 2);
  }

  // Методы (поведение)
  void update() {
    x += vx;
    y += vy;
    if (x < 0 || x > width) vx *= -1;
    if (y < 0 || y > height) vy *= -1;
  }

  void display() {
    fill(100, 150, 255, 150);
    noStroke();
    ellipse(x, y, r * 2, r * 2);
  }
}
```

### 16.3 Создание объектов

Объекты создаются через `new`:

```java
Ball b1;                     // Объявление переменной
b1 = new Ball(100, 200);     // Создание объекта

Ball b2 = new Ball(300, 150);
```

### 16.4 Использование объектов

```java
void setup() {
  size(400, 300);
}

void draw() {
  background(255);
  b1.update();
  b1.display();
  b2.update();
  b2.display();
}
```

### 16.5 Массив объектов

```java
Ball[] balls = new Ball[10];

void setup() {
  size(400, 300);
  for (int i = 0; i < balls.length; i++) {
    balls[i] = new Ball(random(width), random(height));
  }
}

void draw() {
  background(255);
  for (Ball b : balls) {
    b.update();
    b.display();
  }
}
```

### 16.6 Пример: вращающиеся квадраты

```java
class RotatingBox {
  float x, y, size, angle, speed;

  RotatingBox(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
    this.angle = random(TWO_PI);
    this.speed = random(0.01, 0.05);
  }

  void update() {
    angle += speed;
  }

  void display() {
    pushMatrix();
    translate(x, y);
    rotate(angle);
    fill(map(speed, 0.01, 0.05, 100, 255), 100, 200);
    rectMode(CENTER);
    rect(0, 0, size, size);
    popMatrix();
  }
}

RotatingBox[] boxes = new RotatingBox[20];

void setup() {
  size(600, 400);
  for (int i = 0; i < boxes.length; i++) {
    boxes[i] = new RotatingBox(
      random(width), random(height), random(20, 60)
    );
  }
}

void draw() {
  background(30);
  for (RotatingBox box : boxes) {
    box.update();
    box.display();
  }
}
```

### 16.7 Методы, возвращающие значение

```java
class Thermometer {
  float value;

  Thermometer(float initial) {
    value = initial;
  }

  void update(float newValue) {
    value = newValue;
  }

  color getColor() {
    return lerpColor(color(0, 0, 255), color(255, 0, 0), value / 100.0);
  }

  String getLabel() {
    return nf(value, 0, 1) + "°C";
  }
}
```

<details>
<summary><b>Упражнения к разделу 16</b></summary>

1. **Практика.** Создайте класс `Car` с полями x, y, speed, bodyColor. Метод `display()` рисует машинку (кузов + колёса). Создайте 5 машин, движущихся вправо с разными скоростями.
2. **Практика.** Реализуйте класс `Star`: поля x, y, size, brightness, twinkleSpeed. Звезда должна мерцать (изменять brightness по sin). Создайте массив из 50 звёзд на случайных позициях.
3. **Практика.** Добавьте в класс `Ball` метод `applyForce(PVector force)` и реализуйте гравитацию и отталкивание от стен. Создайте 3 шара с разными массами.

</details>

---

## 17. Векторы и PVector

Для работы с движением, физикой и направлениями Processing предоставляет класс `PVector`.

### 17.1 Что такое вектор?

**Вектор** — это направленный отрезок, имеющий длину (magnitude) и направление (heading). В двумерном пространстве вектор задаётся двумя компонентами: x и y.

### 17.2 Создание PVector

```java
PVector v1 = new PVector(3, 4);          // Вектор (3, 4)
PVector v2 = new PVector(mouseX, mouseY); // Вектор от начала координат до мыши
PVector v3 = PVector.random2D();          // Случайное направление, длина 1
```

### 17.3 Базовые операции

```java
PVector a = new PVector(10, 20);
PVector b = new PVector(30, 40);

PVector sum = PVector.add(a, b);       // Сложение: (40, 60)
PVector diff = PVector.sub(a, b);      // Вычитание: (-20, -20)
PVector scaled = PVector.mult(a, 2);   // Умножение на скаляр: (20, 40)

float len = a.mag();                   // Длина вектора: sqrt(10² + 20²)
a.setMag(50);                          // Установить длину в 50
a.normalize();                         // Привести к единичной длине

float d = a.dist(b);                   // Расстояние между a и b (статические)
float d2 = a.dist(b);                  // Или экземплярный метод
```

### 17.4 Движение с ускорением

Классическая схема движения: **позиция + скорость + ускорение**

```java
PVector position;
PVector velocity;
PVector acceleration;

void setup() {
  size(400, 300);
  position = new PVector(width / 2, height / 2);
  velocity = new PVector(0, 0);
}

void draw() {
  background(255);

  // Ускорение направлено к мыши
  PVector mouse = new PVector(mouseX, mouseY);
  PVector direction = PVector.sub(mouse, position);
  direction.setMag(0.1);
  acceleration = direction;

  velocity.add(acceleration);
  velocity.limit(5);        // Ограничение максимальной скорости
  position.add(velocity);

  fill(100, 150, 255);
  ellipse(position.x, position.y, 30, 30);

  // Вектор скорости
  stroke(255, 0, 0);
  line(position.x, position.y,
       position.x + velocity.x * 10,
       position.y + velocity.y * 10);
}
```

### 17.5 Отталкивание от мыши

```java
PVector pos;
PVector vel;

void setup() {
  size(400, 300);
  pos = new PVector(width / 2, height / 2);
  vel = new PVector(1, 2);
}

void draw() {
  background(255);

  // Сила отталкивания от мыши
  PVector mouse = new PVector(mouseX, mouseY);
  PVector repel = PVector.sub(pos, mouse);
  float dist = repel.mag();
  if (dist < 100) {
    repel.setMag(map(dist, 0, 100, 0.5, 0));
    vel.add(repel);
  }

  vel.limit(4);
  pos.add(vel);

  // Границы
  if (pos.x < 0 || pos.x > width) vel.x *= -1;
  if (pos.y < 0 || pos.y > height) vel.y *= -1;

  fill(200, 100, 100);
  ellipse(pos.x, pos.y, 30, 30);
}
```

### 17.6 PVector.fromAngle()

```java
PVector direction;
float angle = 0;

void setup() {
  size(400, 300);
  direction = PVector.fromAngle(0);
}

void draw() {
  background(255);

  direction = PVector.fromAngle(angle);
  direction.mult(100);

  PVector center = new PVector(width / 2, height / 2);
  PVector tip = PVector.add(center, direction);

  stroke(0);
  line(center.x, center.y, tip.x, tip.y);
  fill(255, 0, 0);
  ellipse(tip.x, tip.y, 10, 10);

  angle += 0.02;
}
```

### 17.7 Полезные методы PVector

```java
PVector v = new PVector(3, 4);

float m = v.mag();            // Длина: 5.0
float h = v.heading();        // Угол в радианах
v.rotate(0.1);                // Поворот вектора
v.limit(10);                  // Ограничить длину
v.setMag(1);                  // Установить длину = 1

PVector r = PVector.random2D();  // Случайный единичный вектор
float dp = a.dot(b);             // Скалярное произведение
```

<details>
<summary><b>Упражнения к разделу 17</b></summary>

1. **Практика.** Реализуйте «рой» из 20 точек, каждая из которых движется к цели (мыши), но с небольшим случайным смещением. Используйте PVector для каждой точки.
2. **Практика.** Сделайте программу, где объект движется по эллипсу, используя PVector.fromAngle() с разными радиусами по X и Y.
3. **Практика.** Реализуйте гравитационное притяжение: один большой объект (в центре) притягивает маленькие шарики. Сила притяжения обратно пропорциональна квадрату расстояния.

</details>

---

## 18. Работа с изображениями

Processing позволяет загружать, создавать, обрабатывать и сохранять изображения.

### 18.1 Загрузка и отображение

```java
PImage img;

void setup() {
  size(400, 300);
  img = loadImage("photo.jpg");  // Файл в папке data
}

void draw() {
  image(img, 0, 0);             // Оригинальный размер
  // image(img, 0, 0, width, height);  // Масштабирование под окно
}
```

Поддерживаемые форматы: JPG, PNG, GIF, TGA.

### 18.2 Изменение размера

```java
void setup() {
  size(400, 300);
  PImage img = loadImage("large.jpg");
  img.resize(width, height);    // Изменить размер
  image(img, 0, 0);
}
```

### 18.3 Получение и установка пикселей

```java
PImage img;

void setup() {
  size(400, 300);
  img = loadImage("photo.jpg");
}

void draw() {
  image(img, 0, 0);

  // Получить цвет конкретного пикселя
  color c = img.get(mouseX, mouseY);
  fill(c);
  rect(20, 20, 50, 50);
}
```

### 18.4 Прямой доступ к пикселям через `pixels[]`

```java
void setup() {
  size(200, 200);
}

void draw() {
  loadPixels();  // Загружаем пиксели окна в массив pixels[]

  for (int x = 0; x < width; x++) {
    for (int y = 0; y < height; y++) {
      int loc = x + y * width;
      float r = map(x, 0, width, 0, 255);
      float g = map(y, 0, height, 0, 255);
      float b = map(mouseX, 0, width, 0, 255);
      pixels[loc] = color(r, g, b);
    }
  }

  updatePixels();  // Применяем изменения
}
```

### 18.5 Пиксельные эффекты на изображении

```java
PImage img;

void setup() {
  size(400, 300);
  img = loadImage("photo.jpg");
}

void draw() {
  image(img, 0, 0);

  // Фильтры
  if (keyPressed) {
    if (key == '1') filter(GRAY);
    if (key == '2') filter(BLUR, 3);
    if (key == '3') filter(THRESHOLD, 0.5);
    if (key == '4') filter(INVERT);
    if (key == ' ') image(img, 0, 0);  // Сброс
  }
}
```

### 18.6 Создание изображения с нуля

```java
PImage canvas;

void setup() {
  size(400, 300);
  canvas = createImage(400, 300, RGB);
  for (int i = 0; i < canvas.pixels.length; i++) {
    canvas.pixels[i] = color(random(255), random(255), random(255));
  }
  canvas.updatePixels();
}

void draw() {
  image(canvas, 0, 0);
}
```

### 18.7 Режимы наложения

```java
PImage bg;
PImage fg;

void setup() {
  size(400, 300);
  bg = loadImage("bg.jpg");
  fg = loadImage("overlay.png");
}

void draw() {
  image(bg, 0, 0);
  blendMode(ADD);     // Наложение: ADD, SUBTRACT, DARKEST, LIGHTEST, MULTIPLY
  image(fg, 0, 0);
  blendMode(BLEND);   // Возврат к обычному
}
```

### 18.8 Захват экрана и сохранение кадров

```java
void draw() {
  // ... рисование ...

  if (keyPressed && key == 's') {
    save("sketch.png");           // Сохранить текущий кадр
    saveFrame("frame-####.png");  // Сохранить с номером кадра
  }
}
```

`saveFrame("frame-####.png")` автоматически заменяет `####` на номер кадра (`frameCount`).

<details>
<summary><b>Упражнения к разделу 18</b></summary>

1. **Практика.** Загрузите изображение и наложите эффект пикселизации: разбейте картинку на квадраты 10×10 и залейте каждый квадрат средним цветом пикселей внутри него.
2. **Практика.** Используя `pixels[]`, создайте эффект «зеркала»: левая половина изображения отражается в правую половину.
3. **Практика.** Используя `saveFrame()`, создайте GIF-анимацию из 60 кадров: вращающийся разноцветный квадрат.

</details>

---

## 19. Сохранение и загрузка данных

Processing поддерживает сохранение и загрузку данных в различных форматах: текстовые файлы, таблицы, JSON.

### 19.1 Текстовые файлы: `saveStrings()` / `loadStrings()`

```java
void setup() {
  // Сохранение
  String[] lines = { "Первая строка", "Вторая строка", "Третья строка" };
  saveStrings("data.txt", lines);

  // Загрузка
  String[] loaded = loadStrings("data.txt");
  for (String line : loaded) {
    println(line);
  }
}
```

### 19.2 Таблицы: `saveTable()` / `loadTable()`

```java
void setup() {
  // Создание таблицы
  Table table = new Table();
  table.addColumn("name");
  table.addColumn("score");

  TableRow row1 = table.addRow();
  row1.setString("name", "Alice");
  row1.setInt("score", 1500);

  TableRow row2 = table.addRow();
  row2.setString("name", "Bob");
  row2.setInt("score", 1200);

  saveTable(table, "scores.csv");
}

void draw() {
  // Загрузка и отображение
  Table loaded = loadTable("scores.csv", "header");
  for (TableRow row : loaded.rows()) {
    String name = row.getString("name");
    int score = row.getInt("score");
    println(name + ": " + score);
  }
  noLoop();
}
```

### 19.3 JSON: `saveJSONObject()` / `loadJSONObject()`

```java
void saveSettings() {
  JSONObject json = new JSONObject();
  json.setInt("windowWidth", 800);
  json.setInt("windowHeight", 600);
  json.setString("bgColor", "#FFFFFF");
  json.setBoolean("fullscreen", false);

  saveJSONObject(json, "settings.json");
}

void loadSettings() {
  JSONObject json = loadJSONObject("settings.json");
  int w = json.getInt("windowWidth");
  int h = json.getInt("windowHeight");
  println("Размер окна: " + w + "×" + h);
}
```

### 19.4 Сохранение рекордов (пример)

```java
Table scores;

void setup() {
  size(300, 200);

  File f = new File(dataFile("scores.csv").path());
  if (f.exists()) {
    scores = loadTable("scores.csv", "header");
  } else {
    scores = new Table();
    scores.addColumn("name");
    scores.addColumn("score");
    scores.addColumn("date");
  }
}

void draw() {
  background(240);

  // Отображение таблицы рекордов
  textSize(14);
  fill(0);
  text("Топ результатов:", 20, 30);

  int y = 50;
  // Сортировка и вывод
  for (int i = 0; i < min(scores.getRowCount(), 5); i++) {
    String name = scores.getString(i, "name");
    int score = scores.getInt(i, "score");
    text((i + 1) + ". " + name + " — " + score, 20, y);
    y += 20;
  }
}

void addScore(String name, int score) {
  TableRow row = scores.addRow();
  row.setString("name", name);
  row.setInt("score", score);
  row.setString("date", year() + "-" + month() + "-" + day());
  scores.sortReverse("score");
  saveTable(scores, "scores.csv");
}

void mousePressed() {
  addScore("Player", int(random(1000)));
}
```

### 19.5 Сохранение массива объектов в JSON

```java
class Particle {
  float x, y;
  float size;

  Particle(float x, float y, float size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }

  JSONObject toJSON() {
    JSONObject json = new JSONObject();
    json.setFloat("x", x);
    json.setFloat("y", y);
    json.setFloat("size", size);
    return json;
  }
}

void saveParticles(Particle[] particles, String filename) {
  JSONArray arr = new JSONArray();
  for (int i = 0; i < particles.length; i++) {
    arr.setJSONObject(i, particles[i].toJSON());
  }
  saveJSONArray(arr, filename);
}
```

### 19.6 Диалоги выбора файлов

Processing предоставляет диалоги для выбора файлов через `selectInput()`, `selectOutput()` и `selectFolder()`:

```java
void setup() {
  size(400, 300);
}

void draw() {
  background(240);
  fill(0);
  text("Нажмите клавишу O для открытия файла", 20, 50);
  text("Нажмите клавишу S для сохранения", 20, 80);
}

void keyPressed() {
  if (key == 'o' || key == 'O') {
    selectInput("Выберите файл:", "fileSelected");
  }
  if (key == 's' || key == 'S') {
    selectOutput("Сохранить как:", "fileSaved");
  }
}

void fileSelected(File selection) {
  if (selection != null) {
    println("Выбран файл: " + selection.getAbsolutePath());
    String[] data = loadStrings(selection.getAbsolutePath());
    for (String line : data) {
      println(line);
    }
  }
}

void fileSaved(File selection) {
  if (selection != null) {
    String[] lines = { "Сохранённые данные", "Строка 2" };
    saveStrings(selection.getAbsolutePath(), lines);
    println("Сохранено в: " + selection.getAbsolutePath());
  }
}
```

<details>
<summary><b>Упражнения к разделу 19</b></summary>

1. **Практика.** Создайте приложение-дневник: текстовое поле для ввода, кнопка «Сохранить запись». Все записи храните в файле методом `saveStrings()` / `loadStrings()`. Показывайте список сохранённых записей на экране.
2. **Практика.** Сделайте таблицу рекордов для игры: имя игрока (ввод с клавиатуры), счёт (случайное число), дата. Сохраняйте в CSV, показывайте топ-5 при запуске.
3. **Практика.** Реализуйте сохранение состояния холста: при нажатии Ctrl+S сохраняйте текущий рисунок как PNG (`save()`), при нажатии Ctrl+O загружайте изображение и продолжайте рисовать поверх.

</details>

---

## 20. Основы Processing + Arduino

В этой главе вы научитесь подключать Arduino к Processing, обмениваться данными и создавать графические интерфейсы для управления устройствами.

### Повторение: Processing для главы 20

В примерах этой главы используются следующие концепции Processing. Если вы их забыли — краткий обзор ниже.

**`setup()` и `draw()`** — базовая структура любого скетча. `setup()` вызывается один раз, `draw()` — 60 раз в секунду.

**`import`** — подключение библиотек. Для Arduino нужна `import processing.serial.*;`.

**`size(w, h)`** — размер окна.

**`map(value, fromLow, fromHigh, toLow, toHigh)`** — переводит число из одного диапазона в другой. Например, `map(analogValue, 0, 1023, 0, 255)` превращает показания потенциометра 0–1023 в 0–255.

**`constrain(value, min, max)`** — ограничивает значение в диапазоне.

**Массивы** — `float[] values = new float[100]` хранит последние 100 значений с датчика.

**`fill(r, g, b)`** — цвет заливки. `background(r, g, b)` — цвет фона.

**`ellipse(x, y, w, h)`** — круг/овал. `rect(x, y, w, h)` — прямоугольник.

**`dist(x1, y1, x2, y2)`** — расстояние между двумя точками.

**`mouseX`, `mouseY`** — координаты мыши. **`mousePressed()`** — вызывается при нажатии.

**`text("текст", x, y)`** — вывод текста. `textAlign(CENTER, CENTER)` — выравнивание.

**Тернарный оператор** — `условие ? значение1 : значение2`. Например, `ledState ? color(0,255,0) : color(255,0,0)`.

### Настройка связи Processing и Arduino

Прежде чем запускать примеры, нужно настроить соединение.

#### Шаг 1: Подключите Arduino к компьютеру через USB.

#### Шаг 2: Узнайте номер COM-порта:

- **Windows**: откройте Диспетчер устройств → Порты (COM и LPT). Найдите `Arduino Uno (COM3)` или аналогичный.
- **macOS**: в терминале: `ls /dev/cu.usbmodem*` или `/dev/cu.usbserial*`.
- **Linux**: `ls /dev/ttyACM*` или `/dev/ttyUSB*`.

#### Шаг 3: Запишите Arduino-скетч.

Перед запуском Processing-скетча нужно загрузить соответствующий скетч в Arduino через Arduino IDE. Каждый пример содержит Arduino-код.

#### Шаг 4: Укажите порт в Processing.

В Processing-скетче замените `"COM3"` на ваш порт. Примеры:
- Windows: `"COM5"`
- macOS: `"/dev/cu.usbmodem14101"`
- Linux: `"/dev/ttyACM0"`

#### Типичные проблемы:

| Проблема                             | Решение                                                  |
| ------------------------------------ | -------------------------------------------------------- |
| `NullPointerException` при Serial    | Проверьте, что Arduino подключён и порт указан правильно  |
| Arduino мигает, но нет данных        | Закройте монитор порта в Arduino IDE (он блокирует порт) |
| Данные приходят с шумом             | Увеличьте `delay()` в Arduino или используйте `bufferUntil` |
| Порт занят                           | Перезагрузите Arduino и запустите скетч заново            |

### Пример 1: Передача данных с Arduino в Processing (График данных с потенциометра)

**Концепции Processing в примере:** `arrays`, `map()`, `serialEvent()`, `beginShape()`/`endShape()`, `vertex()`, `background()`, `text()`.

#### Arduino-скетч

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(A0);
  Serial.println(sensorValue);
  delay(50);
}
```

#### Processing-скетч

```java
import processing.serial.*;    // Подключаем Serial-библиотеку

Serial myPort;                  // Объект для работы с портом
float[] values = new float[100]; // Массив для хранения 100 последних значений
int index = 0;                  // Текущая позиция в массиве

void setup() {
  size(800, 400);
  // Замените "COM3" на ваш порт
  myPort = new Serial(this, "COM3", 9600);
  myPort.bufferUntil('\n');     // Собираем данные до символа новой строки
}

void draw() {
  background(255);

  // Рисуем график: соединяем точки линиями
  stroke(0, 150, 255);
  noFill();
  beginShape();
  for (int i = 0; i < values.length; i++) {
    // map() переводит 0-1023 в 0-height (инвертировано по Y)
    float y = map(values[i], 0, 1023, height, 0);
    vertex(map(i, 0, values.length, 0, width), y);
  }
  endShape();

  // Выводим текущее значение
  fill(0);
  text("Потенциометр: " + values[index], 20, 30);
}

// serialEvent() автоматически вызывается при получении данных из Serial
void serialEvent(Serial p) {
  String data = p.readString().trim();  // Читаем строку, убираем пробелы
  if (data != null) {
    float val = float(data);           // Преобразуем строку в число
    values[index] = val;               // Сохраняем в массив
    index = (index + 1) % values.length; // Циклический индекс
  }
}
```

**Разбор Processing-кода:**

- `import processing.serial.*;` — библиотека для Serial-порта.
- `Serial myPort;` — переменная для работы с портом.
- `bufferUntil('\n')` — накапливает данные, пока не придёт `\n`, затем вызывает `serialEvent()`.
- `serialEvent()` — встроенная функция Processing, срабатывает при получении данных.
- `map(values[i], 0, 1023, height, 0)` — преобразует 0–1023 в диапазон высоты окна.
- `beginShape()` / `vertex()` / `endShape()` — рисует ломаную линию по точкам.

### Пример 2: Управление светодиодом через GUI в Processing

**Концепции Processing в примере:** `ellipse()`, `dist()`, `mousePressed()`, тернарный оператор, `surface.setTitle()`.

#### Arduino-скетч

```cpp
void setup() {
  Serial.begin(9600);
  pinMode(13, OUTPUT);  // Встроенный светодиод на пине 13
}

void loop() {
  if (Serial.available()) {
    char cmd = Serial.read();   // Читаем один символ
    if (cmd == '1') digitalWrite(13, HIGH);  // Включить
    if (cmd == '0') digitalWrite(13, LOW);   // Выключить
  }
}
```

#### Processing-скетч

```java
import processing.serial.*;

Serial myPort;
boolean ledState = false;  // false = выключен, true = включён

void setup() {
  size(300, 200);
  myPort = new Serial(this, "COM3", 9600);
  surface.setTitle("LED Control");  // Заголовок окна
}

void draw() {
  background(220);

  // Тернарный оператор: если ledState true — зелёный, иначе — красный
  fill(ledState ? color(0, 255, 0) : color(255, 0, 0));
  ellipse(width / 2, height / 2, 100, 100);

  fill(0);
  textAlign(CENTER, CENTER);
  text("Нажми на круг, чтобы переключить LED",
       width / 2, height / 2 + 70);
}

void mousePressed() {
  // dist() проверяет, попал ли клик в круг
  if (dist(mouseX, mouseY, width / 2, height / 2) < 50) {
    ledState = !ledState;                         // Переключаем состояние
    myPort.write(ledState ? '1' : '0');           // Отправляем символ
  }
}
```

**Разбор кода:**

- `import processing.serial.*;` — библиотека Serial.
- `ledState ? color(0,255,0) : color(255,0,0)` — если `ledState == true`, зелёный, иначе красный.
- `dist(mouseX, mouseY, cx, cy) < r` — проверка клика внутри круга.
- `myPort.write('1')` — отправляет **один байт** (символ '1') в Serial.
- Arduino принимает: `Serial.read()` читает один символ и сравнивает с `'1'` / `'0'`.

### Пример 3: Управление сервоприводом через слайдер в Processing

**Концепции Processing в примере:** библиотека `ControlP5`, слайдер, callback-функция `angle()`.

#### Установка ControlP5

`Скетч → Импорт библиотеки → Добавить библиотеку → найти ControlP5 → Установить`

#### Arduino-скетч

```cpp
#include <Servo.h>

Servo myServo;

void setup() {
  Serial.begin(9600);
  myServo.attach(9);  // Сервопривод на 9 пине
}

void loop() {
  if (Serial.available()) {
    int angle = Serial.parseInt();  // Читаем число из Serial
    myServo.write(angle);           // Поворачиваем серву
  }
}
```

#### Processing-скетч

```java
import processing.serial.*;
import controlP5.*;     // Библиотека для GUI-элементов

Serial myPort;
ControlP5 cp5;          // Объект для управления интерфейсом

void setup() {
  size(400, 300);
  myPort = new Serial(this, "COM3", 9600);
  cp5 = new ControlP5(this);  // Создаём ControlP5

  // Создаём слайдер
  cp5.addSlider("angle")        // Название (совпадает с callback-функцией)
    .setPosition(50, 100)       // Позиция на экране
    .setSize(300, 30)           // Размер
    .setRange(0, 180)           // Диапазон значений
    .setValue(90)               // Начальное значение
    .setCaptionLabel("Угол сервопривода");  // Подпись
}

void draw() {
  background(220);
  fill(0);
  text("Управление сервоприводом", 50, 50);
}

// Callback-функция: ControlP5 автоматически вызывает её
// при изменении слайдера. Имя должно совпадать с названием слайдера.
void angle(int value) {
  myPort.write(value + "\n");  // Отправляем число + перенос строки
}
```

**Разбор кода:**

- `ControlP5` — библиотека для GUI (кнопки, слайдеры, списки). Устанавливается отдельно.
- `cp5.addSlider("angle")` — слайдер с именем `angle`. Processing ищет функцию `void angle(int value)` и вызывает её при изменении.
- `Serial.parseInt()` в Arduino — читает число из Serial до первого нечислового символа.
- `myPort.write(value + "\n")` — отправляем строку вида `"90\n"`.



## 21. Продвинутые проекты Processing + Arduino

В этой главе вы изучите продвинутые приёмы работы Processing с Arduino: текстовые протоколы, двустороннюю связь, визуализацию данных с датчиков.

### Повторение: Processing для главы 21

В примерах этой главы используются следующие возможности Processing.

**Классы и объекты** — `class Ball { ... }`. Позволяют создавать свои типы данных для организации сложных проектов.

**Строки и их методы:**
- `split(input, separator)` — разбивает строку на массив по разделителю
- `indexOf(char)` — ищет позицию символа в строке
- `substring(start, end)` — вырезает часть строки
- `toInt()` — преобразует строку в целое число
- `trim()` — удаляет пробелы в начале и конце

**Обработка клавиатуры:**
- `keyPressed()` — вызывается при нажатии клавиши
- `key` — содержит нажатый символ
- `keyCode` — код клавиши (UP, DOWN, LEFT, RIGHT)
- `key == ENTER` / `key == BACKSPACE` — проверка спецклавиш

**Тригонометрия для визуализации:**
- `sin(angle)`, `cos(angle)` — синус и косинус угла в радианах
- `radians(degrees)` — переводит градусы в радианы
- `atan2(y, x)` — угол вектора от начала координат до точки (x, y)

**Визуализация данных:**
- `beginShape()` / `vertex()` / `endShape()` — рисование произвольной ломаной
- `map(value, fromLow, fromHigh, toLow, toHigh)` — пересчёт диапазона
- `lerpColor(c1, c2, t)` — плавный переход между цветами

**Таймеры и счётчики кадров:**
- `millis()` — миллисекунды с запуска программы
- `frameCount` — количество прошедших кадров
- `frameRate` — частота кадров (по умолчанию 60)

### Пример 4: Отправка текстовых команд на Arduino

**Концепции Processing:** строки, `split()`, `keyPressed()`, контроллеры мыши (`mousePressed()`), кастомные функции с отрисовкой кнопок.

В отличие от одиночных символов, текстовые команды позволяют передавать сложные инструкции: `LED:1`, `SERVO:90`, `RGB:255,0,0`.

#### Arduino-скетч (парсинг команд)

```cpp
void setup() {
  Serial.begin(9600);
  pinMode(13, OUTPUT);
}

void loop() {
  if (Serial.available() > 0) {
    // Serial.readStringUntil('\n') читает строку до символа \n
    String command = Serial.readStringUntil('\n');
    command.trim();

    if (command.startsWith("LED:")) {
      int value = command.substring(4).toInt();
      digitalWrite(13, value == 1 ? HIGH : LOW);
      Serial.println("LED:OK");
    }
    else if (command.startsWith("SERVO:")) {
      int angle = command.substring(6).toInt();
      // myServo.write(angle); — при подключённом сервоприводе
      Serial.println("SERVO:OK");
    }
    else if (command.startsWith("RGB:")) {
      String rgbStr = command.substring(4);
      int comma1 = rgbStr.indexOf(',');
      int comma2 = rgbStr.indexOf(',', comma1 + 1);
      int r = rgbStr.substring(0, comma1).toInt();
      int g = rgbStr.substring(comma1 + 1, comma2).toInt();
      int b = rgbStr.substring(comma2 + 1).toInt();
      Serial.println("RGB:OK");
    }
    else {
      Serial.println("ERROR:UNKNOWN_COMMAND");
    }
  }
}
```

**Разбор Arduino-кода:**
- `Serial.readStringUntil('\n')` — читает данные из Serial buffer до символа новой строки.
- `command.startsWith("LED:")` — проверяет префикс.
- `command.substring(4).toInt()` — извлекает число из строки после 4 символа.
- `indexOf(',')` — находит позицию запятой для разбора RGB.

#### Processing-скетч (панель управления)

```java
import processing.serial.*;

Serial myPort;
String sendValue = "";
boolean inputMode = false;
String receivedData = "";

void setup() {
  size(400, 370);
  myPort = new Serial(this, "COM3", 9600);
  surface.setTitle("Терминал команд");
}

void draw() {
  background(240);

  // Поле ввода
  fill(255);
  stroke(inputMode ? color(100, 150, 255) : color(180));
  strokeWeight(2);
  rect(20, 80, 360, 40, 5);

  fill(0);
  textAlign(LEFT, CENTER);
  textSize(18);
  // Мигающий курсор: каждые 15 кадров переключается видимость
  String cursor = (inputMode && frameCount % 30 < 15) ? "|" : "";
  text(sendValue + cursor, 30, 100);

  fill(100);
  textSize(14);
  text("Введите команду и нажмите ENTER", 20, 50);
  text("Примеры: LED:1, LED:0, SERVO:90, RGB:255,0,0", 20, 170);

  // Кнопки-шорткаты (первый ряд — LED и SERVO)
  drawShortcut(20, 200, 70, 30, "LED ON", "LED:1");
  drawShortcut(100, 200, 70, 30, "LED OFF", "LED:0");
  drawShortcut(180, 200, 90, 30, "SERVO 90", "SERVO:90");
  drawShortcut(280, 200, 90, 30, "SERVO 0", "SERVO:0");

  // Второй ряд — RGB цвета
  drawShortcut(20, 250, 90, 30, "RGB RED", "RGB:255,0,0");
  drawShortcut(120, 250, 90, 30, "RGB GREEN", "RGB:0,255,0");
  drawShortcut(220, 250, 90, 30, "RGB BLUE", "RGB:0,0,255");

  // Вывод ответа от Arduino
  fill(50);
  textAlign(LEFT, TOP);
  textSize(12);
  text("Ответ Arduino: " + receivedData, 20, 320);
}

void drawShortcut(int x, int y, int w, int h, String label, String cmd) {
  boolean hover = mouseX > x && mouseX < x + w && mouseY > y && mouseY < y + h;
  fill(hover ? 200 : 220);
  stroke(180);
  rect(x, y, w, h, 4);
  fill(0);
  textAlign(CENTER, CENTER);
  textSize(12);
  text(label, x + w / 2, y + h / 2);
}

void mousePressed() {
  inputMode = (mouseX > 20 && mouseX < 380 && mouseY > 80 && mouseY < 120);

  if (mouseY >= 200 && mouseY <= 230) {
    if (mouseX > 20 && mouseX < 90)      sendCommand("LED:1");
    else if (mouseX > 100 && mouseX < 170) sendCommand("LED:0");
    else if (mouseX > 180 && mouseX < 270) sendCommand("SERVO:90");
    else if (mouseX > 280 && mouseX < 370) sendCommand("SERVO:0");
  }
  if (mouseY >= 250 && mouseY <= 280) {
    if (mouseX > 20 && mouseX < 110)     sendCommand("RGB:255,0,0");
    else if (mouseX > 120 && mouseX < 210) sendCommand("RGB:0,255,0");
    else if (mouseX > 220 && mouseX < 310) sendCommand("RGB:0,0,255");
  }
}

void keyPressed() {
  if (inputMode) {
    if (key == ENTER || key == RETURN) {
      sendCommand(sendValue);
      sendValue = "";
    } else if (key == BACKSPACE && sendValue.length() > 0) {
      sendValue = sendValue.substring(0, sendValue.length() - 1);
    } else if (key != CODED) {
      sendValue += key;
    }
  }
}

void sendCommand(String cmd) {
  println("Отправка: " + cmd);
  myPort.write(cmd + "\n");
}

void serialEvent(Serial p) {
  receivedData = p.readString().trim();
}
```

**Как это работает:**
1. Пользователь вводит текстовую команду (например, `LED:1`) и нажимает Enter.
2. Processing отправляет: `myPort.write("LED:1\n")`.
3. Arduino получает через `Serial.readStringUntil('\n')`, проверяет префикс и выполняет действие.
4. Arduino отправляет подтверждение (`LED:OK`), Processing отображает его.
5. Кнопки-шорткаты отправляют команды одним кликом.

### Пример 5: Двусторонняя связь — опрос датчиков по запросу

**Концепции Processing:** `keyPressed()`, кнопки мыши, `serialEvent()`, функция `split()`.

Вместо непрерывного потока данных можно опрашивать датчики только когда нужно.

#### Processing-скетч

```java
import processing.serial.*;

Serial myPort;
String sensorData = "Нажмите R для запроса";

void setup() {
  size(400, 300);
  myPort = new Serial(this, "COM3", 9600);
  surface.setTitle("Опрос датчиков");
}

void draw() {
  background(240);
  fill(0);
  textSize(16);
  text("Данные с Arduino:", 20, 50);
  textSize(14);
  text(sensorData, 20, 100);

  // Кнопка запроса (прямоугольник + текст)
  fill(100, 150, 255);
  rect(20, 200, 120, 40, 5);
  fill(255);
  textAlign(CENTER, CENTER);
  text("Запросить (R)", 80, 220);
}

void keyPressed() {
  if (key == 'r' || key == 'R') {
    myPort.write("READ\n");
  }
}

void mousePressed() {
  if (mouseX > 20 && mouseX < 140 && mouseY > 200 && mouseY < 240) {
    myPort.write("READ\n");
  }
}

void serialEvent(Serial p) {
  String data = p.readString().trim();
  if (data != null && data.length() > 0) {
    sensorData = data;
    // При желании: String[] parts = split(data, " | ");
    println("Получено: " + data);
  }
}
```

#### Arduino-скетч

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  if (Serial.available() > 0) {
    String cmd = Serial.readStringUntil('\n');
    cmd.trim();

    if (cmd.equals("READ")) {
      Serial.print("A0:");
      Serial.print(analogRead(A0));
      Serial.print(" | A1:");
      Serial.print(analogRead(A1));
      Serial.print(" | A2:");
      Serial.println(analogRead(A2));
    }
  }
}
```

**Как это работает:**
1. Пользователь нажимает R (или кнопку) — Processing отправляет `READ`.
2. Arduino получает команду, читает все аналоговые пины и отправляет одной строкой.
3. Processing принимает в `serialEvent()` и выводит на экран.

### Пример 6: Ультразвуковой дальномер HC-SR04 + Визуализация

**Концепции Processing:** `arc()`, `map()`, `colorMode(HSB)`, `translate()`, тригонометрия.

HC-SR04 измеряет расстояние от 2 до 400 см методом эхолокации.

#### Схема подключения:

| HC-SR04 | Arduino |
|---------|---------|
| VCC     | 5V      |
| GND     | GND     |
| TRIG    | 9       |
| ECHO    | 10      |

#### Arduino-скетч

```cpp
const int TRIG = 9;
const int ECHO = 10;

void setup() {
  Serial.begin(9600);
  pinMode(TRIG, OUTPUT);
  pinMode(ECHO, INPUT);
}

void loop() {
  digitalWrite(TRIG, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG, LOW);

  long duration = pulseIn(ECHO, HIGH);
  float distance = duration * 0.034 / 2;  // см

  Serial.println(distance);
  delay(200);
}
```

**Разбор:** `pulseIn(ECHO, HIGH)` замеряет длительность импульса в микросекундах. Скорость звука ~340 м/с = 0.034 см/мкс. Делим на 2, так как сигнал идёт туда и обратно.

#### Processing-скетч (радар)

```java
import processing.serial.*;

Serial myPort;
float distance = 0;
float angle = 0;

void setup() {
  size(500, 500);
  myPort = new Serial(this, "COM3", 9600);
  myPort.bufferUntil('\n');
  colorMode(HSB, 360, 100, 100);
}

void draw() {
  background(0);
  translate(width / 2, height - 50);  // Начало координат — внизу по центру

  // Шкалы радара (полукруги)
  noFill();
  stroke(60);
  strokeWeight(1);
  for (int r = 50; r <= 200; r += 50) {
    arc(0, 0, r * 2, r * 2, PI, TWO_PI);
  }

  // Точка обнаружения
  if (distance > 0) {
    float d = constrain(map(distance, 0, 50, 0, 200), 0, 200);
    float hue = map(distance, 5, 50, 0, 120);  // 0=красный, 120=зелёный
    stroke(hue, 100, 100);
    strokeWeight(8);

    float px = cos(radians(angle - 90)) * d;
    float py = sin(radians(angle - 90)) * d;
    point(px, py);
  }

  // Вращающийся луч
  stroke(0, 100, 100, 50);
  strokeWeight(2);
  line(0, 0, cos(radians(angle - 90)) * 200, sin(radians(angle - 90)) * 200);

  angle = (angle + 2) % 360;

  // Текст
  resetMatrix();
  fill(255);
  textAlign(CENTER, TOP);
  textSize(16);
  text("Расстояние: " + nf(distance, 0, 1) + " см", width / 2, 20);
}

void serialEvent(Serial p) {
  String data = p.readString().trim();
  if (data != null && data.length() > 0) {
    float val = float(data);
    if (val > 0) distance = val;
  }
}
```

**Разбор Processing-кода:**
- `translate(width/2, height-50)` — перенос начала координат для удобства отрисовки радара.
- `arc(0, 0, r*2, r*2, PI, TWO_PI)` — полукруг (верхняя половина).
- `cos(radians(angle)) * d` — вычисление координат точки под углом.

### Пример 7: Датчик температуры DHT11 с графиком

**Концепции Processing:** `rect()` для столбцов, `lerpColor()`, массивы-кольцевые буферы, `split()`.

DHT11 — цифровой датчик температуры (0–50°C) и влажности (20–90%).

#### Схема подключения:

| DHT11 | Arduino |
|-------|---------|
| VCC   | 5V      |
| GND   | GND     |
| DATA  | 7       |

Между DATA и VCC желателен резистор 10 кОм.

#### Arduino-скетч

```cpp
#include <DHT.h>

#define DHTPIN 7
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  if (!isnan(temperature) && !isnan(humidity)) {
    Serial.print(temperature);
    Serial.print(" ");
    Serial.println(humidity);
  }

  delay(2000);
}
```

**Разбор:** `dht.readTemperature()` возвращает температуру в °C, `dht.readHumidity()` — влажность в %. `isnan()` проверяет, что значения корректны.

#### Processing-скетч (график температуры и влажности)

```java
import processing.serial.*;

Serial myPort;
float temperature = 0;
float humidity = 0;

// Кольцевой буфер на 60 значений
float[] tempHistory = new float[60];
float[] humHistory = new float[60];
int historyIndex = 0;

void setup() {
  size(600, 400);
  myPort = new Serial(this, "COM3", 9600);
  myPort.bufferUntil('\n');
  surface.setTitle("Монитор температуры и влажности");
}

void draw() {
  background(240);

  // Текущие значения (левый столбец)
  textSize(14);
  fill(0);
  text("Температура", 30, 30);
  textSize(36);
  fill(lerpColor(color(0, 100, 255), color(255, 50, 0),
       constrain(temperature / 40, 0, 1)));
  text(nf(temperature, 0, 1) + "°C", 30, 80);

  textSize(14);
  fill(0);
  text("Влажность", 30, 130);
  textSize(36);
  fill(0, 100, 200);
  text(nf(humidity, 0, 1) + "%", 30, 180);

  // График (правый столбец)
  int gx = 200, gy = 30, gw = 370, gh = 340;
  fill(255);
  stroke(200);
  rect(gx, gy, gw, gh);

  // Температура — красная линия
  stroke(255, 50, 0);
  strokeWeight(2);
  noFill();
  beginShape();
  for (int i = 0; i < tempHistory.length; i++) {
    int idx = (historyIndex + i) % tempHistory.length;
    float x = map(i, 0, tempHistory.length - 1, gx, gx + gw);
    float y = map(tempHistory[idx], 0, 50, gy + gh, gy);
    vertex(x, y);
  }
  endShape();

  // Влажность — синяя линия
  stroke(0, 100, 200);
  beginShape();
  for (int i = 0; i < humHistory.length; i++) {
    int idx = (historyIndex + i) % humHistory.length;
    float x = map(i, 0, humHistory.length - 1, gx, gx + gw);
    float y = map(humHistory[idx], 0, 100, gy + gh, gy);
    vertex(x, y);
  }
  endShape();

  // Легенда
  noStroke();
  fill(255, 50, 0);
  textSize(12);
  textAlign(LEFT, TOP);
  text("Температура", gx + 10, gy + 10);
  fill(0, 100, 200);
  text("Влажность", gx + 10, gy + 30);
}

void serialEvent(Serial p) {
  String data = p.readString().trim();
  if (data != null && data.length() > 0) {
    // split() разбивает строку на две части: "25.3 60.1"
    String[] parts = split(data, ' ');
    if (parts.length >= 2) {
      temperature = float(parts[0]);
      humidity = float(parts[1]);

      // Кольцевой буфер: сохраняем и сдвигаем индекс
      tempHistory[historyIndex] = temperature;
      humHistory[historyIndex] = humidity;
      historyIndex = (historyIndex + 1) % tempHistory.length;
    }
  }
}
```

**Разбор Processing-кода:**
- `split(data, ' ')` — разбивает строку `"25.3 60.1"` на массив `["25.3", "60.1"]`.
- `lerpColor(blue, red, t)` — плавный переход от синего к красному в зависимости от температуры.
- Кольцевой буфер: последние 60 значений хранятся в массиве; `historyIndex` циклически перезаписывает старые данные.
- `beginShape()` / `vertex()` / `endShape()` строит линию графика по точкам.

#### Сводка методов передачи данных

| Метод                     | Пример команды              | Когда использовать                    |
| ------------------------- | --------------------------- | ------------------------------------- |
| Одиночный символ          | `'1'` / `'0'`               | Простое управление (вкл/выкл)         |
| Число                     | `90\n`                     | Одно числовое значение                |
| Текстовая команда         | `LED:1\n`                  | Несколько разных устройств            |
| Протокол с подтверждением | `LED:1` → `LED:OK`         | Критичные команды, нужна обратная связь |
| Пакетный опрос            | `READ` → `"A0:512 A1:234"`  | Получение группы данных по запросу    |
| Два числа через пробел    | `"25.3 60.1"`               | Передача пары связанных значений      |

<details>
<summary><b>Упражнения к разделу 21</b></summary>

1. **Практика.** Модифицируйте Пример 4: добавьте кнопку «Очистить» и отображение истории отправленных команд (последние 10).
2. **Практика.** В Примере 6 (радар) сохраняйте последние 30 измерений и рисуйте их все, создавая карту препятствий. Используйте массив для хранения истории.
3. **Практика.** В Примере 7 (DHT11) добавьте визуальный индикатор: если температура выше 30°C — фон красный, если ниже 10°C — синий. Используйте класс из главы 16.

</details>

---

## 22. Итоговый проект: Paint

Закрепим изученное — создадим полноценное приложение-рисовалку.

```java
int brushColor = color(0);
int brushSize = 5;
boolean isDrawing = false;
boolean eraserMode = false;

void setup() {
  size(800, 600);
  background(255);
}

void draw() {
  if (isDrawing) {
    if (eraserMode) {
      stroke(255);
    } else {
      stroke(brushColor);
    }
    strokeWeight(brushSize);
    line(mouseX, mouseY, pmouseX, pmouseY);
  }

  drawPalette();
}

void mousePressed() {
  if (mouseY < height - 50) {
    isDrawing = true;
  } else {
    if (mouseX < width / 5) {
      brushColor = color(255, 0, 0);
    } else if (mouseX < 2 * width / 5) {
      brushColor = color(0, 255, 0);
    } else if (mouseX < 3 * width / 5) {
      brushColor = color(0, 0, 255);
    } else if (mouseX < 4 * width / 5) {
      brushColor = color(255, 255, 0);
    } else {
      brushColor = color(0);
    }
  }
}

void mouseReleased() {
  isDrawing = false;
}

void drawPalette() {
  fill(255);
  rect(0, height - 50, width, 50);

  fill(255, 0, 0);
  rect(0, height - 50, width / 5, 50);

  fill(0, 255, 0);
  rect(width / 5, height - 50, width / 5, 50);

  fill(0, 0, 255);
  rect(2 * width / 5, height - 50, width / 5, 50);

  fill(255, 255, 0);
  rect(3 * width / 5, height - 50, width / 5, 50);

  fill(0);
  rect(4 * width / 5, height - 50, width / 5, 50);

  fill(brushColor);
  ellipse(width - 50, height - 25, brushSize * 2, brushSize * 2);

  fill(200);
  rect(width - 100, height - 50, 100, 50);
  fill(0);
  textAlign(CENTER, CENTER);
  text("Ластик", width - 50, height - 25);
}

void mouseWheel(MouseEvent event) {
  brushSize += event.getCount();
  brushSize = constrain(brushSize, 1, 50);
}

void mouseClicked() {
  if (mouseX > width - 100 && mouseX < width && mouseY > height - 50 && mouseY < height) {
    eraserMode = !eraserMode;
  }
}
```

### Разбор ключевых моментов:

1. **`setup()`** — задаёт размер окна и белый фон.
2. **`draw()`** — проверяет, рисуем ли мы (`isDrawing`), и проводит линию от предыдущей позиции к текущей.
3. **Обработка мыши** — `mousePressed()` переключает цвет или включает рисование; `mouseWheel()` меняет размер кисти; `mouseClicked()` включает ластик.
4. **Палитра** — 5 цветных кнопок внизу экрана.
5. **Ластик** — переключает цвет обводки на белый.

<details>
<summary><b>Упражнения к разделу 22</b></summary>

1. **Модификация.** Добавьте в Paint возможность сохранять рисунок в файл при нажатии клавиши `S` (используйте `saveFrame("sketch.png")`).
2. **Модификация.** Добавьте в палитру кнопку выбора произвольного цвета через стандартный пикер (используйте библиотеку `ColorPicker` или просто добавьте больше предустановленных цветов).
3. **Модификация.** Добавьте отображение текущих координат мыши в правом верхнем углу экрана.

</details>

---

## 23. Заключение

Processing — мощный и доступный инструмент для создания визуальных проектов. С помощью простого синтаксиса и богатого набора встроенных функций вы можете быстро реализовать свои идеи — от простых рисунков до сложной анимации и интерактивных приложений.

### Что дальше?

- **Официальная документация**: [processing.org/reference/](https://processing.org/reference/)
- **Библиотеки**: Processing поддерживает множество библиотек — для работы со звуком, видео, компьютерным зрением, физикой и т.д.
- **Сообщество**: тысячи примеров на [openprocessing.org](https://openprocessing.org/) и [processing.org/examples/](https://processing.org/examples/)

Помните: лучший способ научиться программировать — практиковаться. Экспериментируйте, модифицируйте примеры, придумывайте свои проекты!
