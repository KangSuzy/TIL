# π΅ Django review π΅

### ν¨ν€μ§ μ’μμ± κ΄λ¦¬
κ³΅λ μμμ **install ν ν¨ν€μ§κ° μμ΄ν κ²½μ°** merge ν λ λ¬Έμ κ° λ°μνλ€ !

μμνκ²½μμ μ΄λ€ ν¨ν€μ§λ€μ μ¬μ©νκ³  μλμ§ νμΌλ‘ λκ²¨μ£ΌκΈ° μν΄ μλμ λͺλ Ήμ΄λ₯Ό μ¬μ©
```
pip freeze > requirements.txt
```

μλ ν¨ν€μ§λ₯Ό νλ²μ λ€μ΄λ‘λνκΈ° μν΄μλ μλμ λͺλ Ήμ΄λ₯Ό μ¬μ©
```
pip install -r requirements.txt
```

### Django MySQL
- ν¨ν€μ§ λ€μ΄λ‘λ
```
pip install pymysql
```

- settings.py μμ 
```python
# μ΅μλ¨
import pymysql
pymysql.install_as_MySQLdb()
```
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '', # db λͺ
        'USER' : '', # μ¬μ©μλͺ
        'PASSWORD':'', # λΉλ°λ²νΈ
    }
}
```

- migrate λ°μ
```
python manage.py migrate
```
- μ€ν μ€λ₯μ
```
pip install mysqlclient
```

### settings.py SECRET_KEY λΆλ¦¬

μ mysql password μ django secret key λ₯Ό my_settings.py νμΌμ μμ±νκ³ 

.gitignore μ μ¬λ¦¬μ !
