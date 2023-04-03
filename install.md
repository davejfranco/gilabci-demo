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

### versionar codigo con git
```shell
git init
git add .
git commit -m "first commit"
git branch -M master
git remote add origin git@gitlab.com:demo5085013/python-fastapi.git
git push -u origin master
```

