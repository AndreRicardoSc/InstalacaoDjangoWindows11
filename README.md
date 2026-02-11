# Tutorial de Instalação do Django no Windows 11 (2026) :globe_with_meridians:

## 01 - Instalação do Python :snake:

### Instalador

Primeiro precisaremos instalar o [Python 3.14.3 - Feb. 3, 2026](https://www.python.org/ftp/python/3.14.3/python-3.14.3-amd64.exe) (última versão)

Execute o arquivo que você baixou e na tela que exibir, clique na opção **Customize Instalation**

Pode deixar tudo como está configurado, porém, preste atenção no caminho que o Python será instalado, se parecerá com isso:

~~~
C:\Users\SEU USUÁRIO\AppData\Local\Programs\Python\Python314\
~~~

> Substitua **SEU USUÁRIO** pelo nome do usuário que estiver na sua máquina

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
python --version
~~~


---


## Instalação do PDM (Python Package and Dependency Manager) :computer:




