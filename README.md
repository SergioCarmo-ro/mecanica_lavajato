
# MECANICA_LAVAJATO 😄🔧🚗💦

## Descrição Breve do Sistema
😄 **APLICAÇÃO OFICINAS E LAVA JATOS com Python e Django**  
MECANICA_LAVAJATO é um sistema para auxiliar oficinas mecânicas que ofereçam serviços de lavagem de veículos, combinando serviços de reparo e manutenção automotiva com limpeza e estética de veículos. Com interface intuitiva para cadastrar clientes e seus veículos, emitindo ordens de serviços com descrições de peças e reparos. O sistema é desenvolvido com as ferramentas de programação Python 🐍, Django 🌐, HTML 📄, CSS 🎨 e JavaScript ⚡.

## Arquitetura Resumida
O sistema segue a arquitetura MVC (Model-View-Controller) do Django, com um projeto central (`mecajato`) que gerencia configurações globais e um app dedicado (`clientes`) para funcionalidades específicas de cadastro de clientes e veículos. Os arquivos estáticos e mídia são servidos via configurações no `settings.py`, permitindo upload de imagens de veículos e documentos de ordens de serviço. A comunicação entre views, URLs e templates é simplificada para um fluxo intuitivo: requisições HTTP → views → templates HTML com CSS/JS para frontend responsivo.

## Estrutura Simplificada
```
mecajato/
├── manage.py
├── mecajato/
│   ├── __init__.py
│   ├── settings.py          # Configurações (STATIC, MEDIA, apps)
│   ├── urls.py              # URLs principais (inclui app clientes)
│   └── wsgi.py
├── clientes/                # App para clientes e veículos
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── migrations/
│   ├── models.py            # Modelos para Cliente e Veículo
│   ├── tests.py
│   ├── urls.py              # URLs do app (ex: path('', views.clientes))
│   └── views.py             # Views (ex: def clientes(request))
├── media/                   # Uploads (imagens de veículos)
├── static/                  # Arquivos estáticos (CSS, JS, imagens)
└── templates/               # Templates HTML para views
    └── static/              # CSS e JS locais
```

## Tecnologias Utilizadas
- 🐍 **Python** - Linguagem principal para backend e lógica de negócio.
- 🌐 **Django** - Framework web para desenvolvimento rápido e seguro.
- 📄 **HTML** - Estrutura das páginas e templates.
- 🎨 **CSS** - Estilos e layout responsivo.
- ⚡ **JavaScript** - Interatividade no frontend (ex: validações em formulários).

## Funcionalidades do Protótipo
- Cadastro de clientes com dados pessoais (nome, contato, endereço).
- Registro de veículos associados (modelo, placa, ano, quilometragem).
- Emissão de ordens de serviço: descrições de reparos, peças necessárias e serviços de lavagem.
- Interface intuitiva para listagem e edição de registros.
- Upload de imagens/mídia para veículos e ordens de serviço.
- Teste básico de views para exibição de lista de clientes.

## Como Executar o Sistema
### Passo 1: Crie o Ambiente Virtual
```bash
python -m venv venv
```

### Passo 2: Ative o venv
- No Windows: `venv\Scripts\activate`
- No Linux/Mac: `source venv/bin/activate`

### Passo 3: Instale o Django e Crie um Projeto Django
```bash
pip install django
django-admin startproject mecajato .
```

### Passo 4: Configure os Arquivos Estáticos (em settings.py)
Adicione no final do arquivo:
```python
import os
STATIC_URL = '/static/'
STATICFILES_DIRS = (os.path.join(BASE_DIR, 'templates/static'),)
STATIC_ROOT = os.path.join('static')

MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
MEDIA_URL = '/media/'
```

### Passo 5: Crie o App Clientes
```bash
python manage.py startapp clientes
```

### Passo 6: Registre o App em settings.py
Adicione `'clientes'` à lista `INSTALLED_APPS`.

### Passo 7: Redirecione uma URL para o App Clientes (em mecajato/urls.py)
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('clientes/', include('clientes.urls')),
]
```

### Passo 8: Crie uma URL para a View (em clientes/urls.py)
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.clientes, name="clientes")
]
```

### Passo 9: Crie a View Clientes (em clientes/views.py)
```python
from django.http import HttpResponse

def clientes(request):
    return HttpResponse('Teste')
```

### Passo 10: Execute as Migrações e Inicie o Servidor
```bash
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```
Acesse `http://127.0.0.1:8000/clientes/` para ver o teste.

## Dependências Utilizadas
- Django (versão instalada via pip, compatível com Python 3.x).
- Bibliotecas padrão do Python (os, django.http).

Para instalação completa: `pip install -r requirements.txt` (crie o arquivo com `pip freeze > requirements.txt` após instalar Django).

## Passo a Passo para Execução
Siga os passos acima sequencialmente. Certifique-se de ter Python 3.8+ instalado. Após configuração, o protótipo roda localmente em modo desenvolvimento.

## Observações Importantes
- Este é um protótipo inicial; adicione autenticação e banco de dados real (SQLite por default) para produção.
- Para upload de mídia, configure o servidor web (ex: Nginx) em deploy.
- Teste em ambiente virtual para evitar conflitos de dependências.
- A view atual retorna apenas um texto de teste; expanda com templates e modelos para funcionalidades completas.

## Status do Projeto
**Protótipo Inicial** - Funcionalidades básicas implementadas (cadastro e views de teste). Em desenvolvimento para inclusão de ordens de serviço e dashboard.

## Autor
**Sérgio Ademir Rocha do Carmo** - Apresento aqui o sistema MECANICA_LAVAJATO adaptado do curso do canal Pytonando como sistema de apoio acadêmico da disciplina Integração e Manutenção de Software do curso de Engenharia de Software da UFAM/ICET. Contato: sergioademircarmo@gmail.com.

