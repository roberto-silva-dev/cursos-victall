
# Tutorial: Criando uma aplicação Django com login básico

## Pré-requisitos

- Python 3.8 ou superior instalado
- `pip` instalado

## (Opcional) Criar um ambiente virtual

```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate   # Windows
```

## Passo 1: Instalar o Django

```bash
pip install django
```

## Passo 2: Criar o projeto

```bash
django-admin startproject core .
# OU
# python -m django startproject core .
```

## Passo 3: Criar o aplicativo principal

```bash
python manage.py startapp main
```

## Passo 4: Configurar o projeto

### Editar `core/settings.py`

1. Adicionar `'main'` em `INSTALLED_APPS`
2. Definir as URLs de redirecionamento após login:

```python
LOGIN_REDIRECT_URL = '/'
LOGOUT_REDIRECT_URL = '/login/'
```

## Passo 5: Criar as views de login/logout e página principal

### `main/views.py`

```python
from django.shortcuts import render
from django.contrib.auth.decorators import login_required

@login_required
def home(request):
    return render(request, 'home.html')
```

## Passo 6: Configurar URLs

### `main/urls.py`

```python
from django.urls import path
from .views import home

urlpatterns = [
    path('', home, name='home'),
]
```

### `core/urls.py`

```python
from django.contrib import admin
from django.urls import path, include
from django.contrib.auth import views as auth_views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('main.urls')),
    path('login/', auth_views.LoginView.as_view(template_name='login.html'), name='login'),
    path('logout/', auth_views.LogoutView.as_view(), name='logout'),
]
```

## Passo 7: Criar os templates

### Criar a pasta `templates/` dentro do app `main`:

```
main/
└── templates/
    ├── login.html
    └── home.html
```

### `login.html`

```html
<h2>Login</h2>
<form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Entrar</button>
</form>
```

### `home.html`

```html
<h2>Bem-vindo, {{ user.username }}!</h2>
<a href="{% url 'logout' %}">Sair</a>
```

## Passo 8: Criar o banco de dados

```bash
python manage.py migrate
```

## Passo 9: Criar o superusuário

```bash
python manage.py createsuperuser
```

## Passo 10: Rodar o servidor

```bash
python manage.py runserver
```

Acesse `http://127.0.0.1:8000/login/` para testar.
