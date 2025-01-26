README.MD
-----------------
Maciej
nr albumu 157116
Informatyka C3
-----------------

# To-Do List w Django

Prosta aplikacja listy zadań ("To-Do List") stworzona w oparciu o framework Django (Python). 
Umożliwia dodawanie, edytowanie, usuwanie oraz oznaczanie zadań jako ukończonych.

--------------------

## Spis treści

1. [Opis projektu]
2. [Wymagania] 
3. [Instalacja i uruchomienie]  
4. [Elementy aplikacji]  
   - [a) Generatory komponentów (modeli, kontrolerów, …)]
   - [b) Routery kierujące ruchem HTTP]
   - [c) Szablony HTML]
   - [d) Konektory do baz-danych]
   - [e) Współpraca z REST API]
5. [Struktura plików]

---

## 1.Opis projektu

Ta aplikacja jest przykładem prostej listy zadań, gdzie użytkownik może:
- Dodawać zadania,  
- Edytować zadania,  
- Zaznaczać zadania jako ukończone,  
- Usuwać zadania,  
- Przeglądać listę wszystkich zadań.

Framework: Django (Python).  
Architektura: MVT (Model-View-Template) – zbliżona do MVC.  

---

## 2.Wymagania

- Python 3.8+ (zalecana 3.10 lub 3.11).  
- Django 3.2+ (lub nowsza).  

## 3.Instalacja i uruchamianie

Sklonuj repozytorium (lub pobierz ZIP) i przejdź do katalogu projektu:
git clone https://github.com/Maciej157116/Zaliczenie_Projektowanie_MVC.git
cd sciezka/do/projektu


Tworzymy/ modyfikujemy tabele w bazie danych (SQLite) komendami:
python manage.py makemigrations
python manage.py migrate

Uruchamiamy serwer:
python manage.py runserver

Domyślny adres naszej aplikacji to:
http://127.0.0.1:8000/


----------------------------------

## 4.Elementy aplikacji
a)Generatory komponentów
W Django korzystamy z wbudowanych generatorów:

django-admin startproject <nazwa_projektu>
Tworzy główną strukturę projektu (katalog, manage.py, pliki konfiguracyjne)

python manage.py startapp <nazwa_aplikacji>
Generuje folder z plikami dla nowej aplikacji, np. tasks/ (z models.py, views.py, urls.py itd.).

Dzięki temu nie trzeba ręcznie tworzyć i konfigurować plików.

b)Routery kierujące ruchem HTTP
Routing w Django opiera się na plikach urls.py
Główny plik (Projekt/urls.py) zawiera podstawowe ścieżki (admin/) i include('tasks.urls').

W tasks/urls.py definiujemy reguły kierujące do odpowiednich widoków (funkcji w views.py).

c)Szablony HTML
Pliki .html znajdują się w folderze tasks/templates/

Widoki korzystają z funkcji render(request, 'szablon.html', context), aby przygotować odpowiedź HTML

System szablonów Django pozwala m.in. na użycie zmiennych, pętli {% for %} oraz tagów {% url '...' %}

d)Konektory do baz danych
Django domyślnie używa SQLite (plik db.sqlite3)

ORM Django zarządza mapowaniem obiektowym, co ułatwia operacje CRUD na modelach (np. Task)

e)Współpraca z REST API
W tej aplikacji nie korzystamy z zewnętrznych API ani nie wystawiamy własnego REST API.

Gdybyśmy chcieli tworzyć endpointy JSON, moglibyśmy wykorzystać Django REST Framework, ale w tej wersji ograniczamy się do widoków HTML
----------------------------------

## 5.Struktura plików

Projekt/
├── Projekt/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── tasks/
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── urls.py
│   ├── views.py
│   └── templates/
│       ├── task_list.html
│       ├── task_create.html
│       └── task_edit.html
├── db.sqlite3
└── manage.py


