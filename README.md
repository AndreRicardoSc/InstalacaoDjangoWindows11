# Tutorial de Instalação do Django no Windows 11 (2026) :globe_with_meridians:

## 01 - Instalação do Python :snake:

### Instalador do Python

Primeiro precisaremos instalar o [Python 3.14.3 - Feb. 3, 2026](https://www.python.org/ftp/python/3.14.3/python-3.14.3-amd64.exe) (última versão)

Execute o arquivo que você baixou e na tela que exibir, clique na opção **Customize Instalation**

Pode deixar tudo como está configurado, porém, preste atenção no caminho que o Python será instalado, se parecerá com isso:

~~~
C:\Users\SEU USUÁRIO\AppData\Local\Programs\Python\Python314\
~~~

> **ATENÇÃO:** Guarde esse caminho com o seu nome de usuário pois iremos usar

---

### Variáveis de ambiente - PATH

Esta parte requer um pouco mais de atenção, procure bem os itens que irei citar

Na sua máquina, digite o atalho `Windows + R` 

Na janela que abriu, escreva `sysdm.cpl` e aperte `Enter`

Você abriu as **Propriedades do Sistema**, depois disso:
- Clique na sequência: `Avançado > Variáveis de Ambiente`
- Na parte de **Variáveis do Sistema**, na coluna **Variável**, procure por `Path`
- Selecione e clique em `Editar`
- Clique em `Novo` e adicione:
~~~
C:\Users\SEU USUÁRIO\AppData\Local\Programs\Python\Python314\
~~~
- Após digitar, apenas clique novamente em `Novo` e adicione:
~~~
C:\Users\SEU USUÁRIO\AppData\Local\Programs\Python\Python314\Scripts\
~~~
- Clique em `Ok` em todas as abas

Depois desses passos, abra um terminal Powershell normalmente e rode:

~~~
python -V
~~~

Se aparecer algo como 3.14.3, Python instalado com sucesso! 

---


## 02 - Instalação do PDM (Python Package and Dependency Manager) :computer:

Depois de instalar o Python, precisamos do gerenciador de pacotes e dependência (PDM)

Para instalar, abra o terminal e digite:
~~~
pip install pdm
~~~
Depois de instalado, feche o terminal, abra novamente e verifique a versão do PDM:
~~~
pdm -V
~~~
Deve aparecer algo como:
> PDM, version 2.26.6

Se estiver em qualquer outra versão, atualize com o comando:
~~~
pip install --upgrade pdm
~~~
Feche, abra o terminal e verifique novamente. Agora sim deve aparecer:
> PDM, version 2.26.6

Se aparecer essa mensagem, PDM foi instalado com sucesso! :white_check_mark:


---


## 03 - Inicialização de projeto com Django :page_facing_up:

Com o PDM instalado, iniciar um novo projeto

- Crie uma pasta para o projeto com o nome que preferir
~~~
mkdir meu_projeto
~~~
- Caminhe até a pasta:
~~~
cd meu_projeto
~~~
- Inicie um projeto com PDM
~~~
pdm init
~~~
- Você passará por uma tela como essa, pode responder como aqui:
~~~
Creating a pyproject.toml for PDM...
Please enter the Python interpreter to use
 0. cpython@3.14 (C:\Users\ZETEC\AppData\Local\Programs\Python\Python314\python.EXE)
 1. cpython@3.13 (C:\Program Files\Python313\python.exe)
Please select (0): 0
Virtualenv is created successfully at D:\01 - ZETEC\Documents\2026\desweb\meu_projeto\.venv
Project name (meu_projeto): meu_projeto
Project version (0.1.0):
Do you want to build this project for distribution(such as wheel)?
If yes, it will be installed by default when running `pdm install`. [y/n] (n): n
License(SPDX name) (MIT):
Author name (AndreRicardoSc):
Author email (andrenarutto7@gmail.com):
Python requires('*' to allow any) (==3.14.*): *
INFO: Git repository initialized successfully.
Project is initialized successfully
~~~
- Depois disso, pode abrir seu projeto no VsCode
~~~
code .
~~~
- Abra um terminal `Ctrl + J` e digite:
~~~
pdm add django
~~~
- Verifique se o arquivo `pdm.lock` foi criado:
~~~
ls -l pdm.lock
~~~
- Se foi criado, inicie um projeto Django:
~~~
pdm run django-admin startproject config .
~~~
- Rode os comandos de migração do banco de dados:

Primeiro, para preparar as migrações:
~~~
pdm run python manage.py makemigrations
~~~

Depois, para executar as migrações:
~~~
pdm run python manage.py migrate
~~~

- Para poder acessar a aba de admin, execute:
~~~
pdm run python manage.py createsuperuser
~~~
Irá se deparar com uma tela dessa:
~~~
Username (leave blank to use 'zetec'): admin
Email address: admin@admin.com
Password: 
Password (again): 
The password is too similar to the username.
This password is too short. It must contain at least 8 characters.
This password is too common.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
~~~
Reponda admin em tudo para maior facilidade de desenvolvimento
- Rode o sistema:
~~~
pdm run python manage.py runserver
~~~
- Se tudo correu bem, o sistema estará rodando na porta:
~~~
http://localhost:8000/
~~~
- Para acessar o admin:
~~~
http://localhost:8000/admin/
~~~
