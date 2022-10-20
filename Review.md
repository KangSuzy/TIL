# 🔵 Django review 🔵

### 패키지 종속성 관리
공동 작업시 **install 한 패키지가 상이한 경우** merge 할때 문제가 발생한다 !

작업환경에서 어떤 패키지들을 사용하고 있는지 파일로 넘겨주기 위해 아래의 명령어를 사용
```
pip freeze > requirements.txt
```

없는 패키지를 한번에 다운로드하기 위해서는 아래의 명령어를 사용
```
pip install -r requirements.txt
```

### Django MySQL
- 패키지 다운로드
```
pip install pymysql
```

- settings.py 수정
```python
# 최상단
import pymysql
pymysql.install_as_MySQLdb()
```
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': '', # db 명
        'USER' : '', # 사용자명
        'PASSWORD':'', # 비밀번호
    }
}
```

- migrate 반영
```
python manage.py migrate
```
- 실행 오류시
```
pip install mysqlclient
```

### settings.py SECRET_KEY 분리

위 mysql password 와 django secret key 를 my_settings.py 파일에 작성하고

.gitignore 에 올리자 !

### 로그인 회원가입 ..

