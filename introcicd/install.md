# Instrucciones 

### Descargar codigo
```shell
wget https://github.com/davejfranco/python-fastapi-demo/archive/refs/heads/base.zip
```

### Descomprimir
```shell
unzip base.zip
```

### Instalar dependencias
```shell
virtualenv .env
source .env/bin/activate
pip install -r requirements.txt
```

### Ejecutar pruebas
```shell
pytest test/test.py
```

### Ejecutar API
```shell
uvicorn app.main:app --reload
```
# Crear proyecto en gitlab
Para crear proyecto en gitlab, debemos ir a la pagina de gitlab y crear un nuevo proyecto. En este caso, el proyecto se llama python-fastapi. Una vez creado el proyecto, vamos a la sección de settings y copiamos la url del proyecto. En este caso, la url es https://gitlab.com/demo5085013/python-fastapi.git

### versionar codigo con git
```shell
git init
git add .
git commit -m "first commit"
git branch -M master
git remote add origin git@gitlab.com:demo5085013/python-fastapi.git
git push -u origin master
```

