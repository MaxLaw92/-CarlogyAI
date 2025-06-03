# Зміна структури посилань для простішої інтеграції з GitHub Pages

Для забезпечення кращої сумісності з GitHub Pages, можна спростити структуру посилань. Давайте реалізуємо альтернативне рішення, яке буде працювати навіть без правильного виявлення базового шляху.

## Оновлення посилань у файлах

### 1. index.html
Змініть посилання в навігаційному меню з:
```html
<a href="business/index.html" class="nav-link" data-lang-key="business-link">
```
на:
```html
<a href="./business.html" class="nav-link" data-lang-key="business-link">
```

та з:
```html
<a href="insurance/index.html" class="nav-link" data-lang-key="insurance-link">
```
на:
```html
<a href="./insurance.html" class="nav-link" data-lang-key="insurance-link">
```

### 2. Перейменування файлів

Замість структури з каталогами:
```
/
├── index.html            
├── business/
│   └── index.html        
├── insurance/
│   └── index.html
```

Використовуйте плоску структуру:
```
/
├── index.html            
├── business.html         
├── insurance.html        
```

Це означає, що вам потрібно:
1. Взяти вміст файлу `business/index.html` і створити новий файл `business.html` у кореневому каталозі
2. Взяти вміст файлу `insurance/index.html` і створити новий файл `insurance.html` у кореневому каталозі

### 3. Оновлення посилань у business.html та insurance.html

У цих файлах також потрібно оновити посилання:

У `business.html`:
```html
<a href="./index.html" class="nav-link">
<a href="./business.html" class="nav-link active">
<a href="./insurance.html" class="nav-link">
```

У `insurance.html`:
```html
<a href="./index.html" class="nav-link">
<a href="./business.html" class="nav-link">
<a href="./insurance.html" class="nav-link active">
```

## Переваги цього підходу

1. Простіша структура - всі файли знаходяться в одному каталозі
2. Немає проблем з відносними шляхами 
3. Працює з будь-яким хостингом без спеціальних налаштувань
4. Не потребує складних скриптів для виявлення базового шляху

## Як це реалізувати

1. Створіть нові файли `business.html` та `insurance.html` з вмістом відповідних index.html з підкаталогів
2. Оновіть всі внутрішні посилання у всіх трьох файлах
3. Завантажте ці три файли в корінь вашого репозиторію
4. Видаліть підкаталоги business та insurance з репозиторію на GitHub (якщо вони вже там є)