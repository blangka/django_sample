# django_basic

django의 기본 적인 구조에 대해서 알아 보는 프로젝트로 시작합니다.  
간단하게 [주식 검색 웹 만들기](https://hmg.udemy.com/course/django-s/learn/lecture/18126411#overview) 강의를 보며 프로젝트를 구성할 예정입니다.  
공식문서로는 [django doc](https://docs.djangoproject.com/ko/4.1/intro/overview) 을 참고하여 기본 구조 및 상세 내용을 프로젝트 진행 하면서 기재할 예정입니다.
개념 설명 참고 자료 : 성

## 가상 환경에서 실행 시키기

   ```bash
        $ virtualenv venv
        $ source venv/bin/activate
   ```   

## django 설치

   ```bash
        $ pip install django
        $ pip list
   ```

## django 프로젝트 시작

1. 프로젝트 생성

    ```bash
          $ django-admin startproject django_stock
          $ cd django_stock
          $ ls
    ```  

2. app 생성
    ```bash
            $ python manage.py startapp stocks
            $ ls
    ```  
   app은 각각 기능별 또는 기능에 따른 기능을 구현하기 위해 생성합니다. 예를 들어 동영상을 처리하는 것이 있고 메일을 보내는 것이 있다면 각각 추가 해주어야 한다.


3. 폴더별 생성된 파일의 설명(django_stock 하위 폴더)
   1. manage.py: Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인의 유틸리티 입니다. manage.py 에 대한 자세한 정보는 django-admin and manage.py 에서 확인할 수 있습니다.  
   2. django_stock/ 디렉토리 내부에는 프로젝트를 위한 실제 Python 패키지들이 저장됩니다. 이 디렉토리 내의 이름을 이용하여, (django_stock.urls 와 같은 식으로) 프로젝트의 어디서나 Python 패키지들을 임포트할 수 있습니다.
   3. django_stock/__init__.py: Python으로 하여금 이 디렉토리를 패키지처럼 다루라고 알려주는 용도의 단순한 빈 파일입니다. Python 초심자라면, Python 공식 홈페이지의 패키지를 읽어보세요.
   4. django_stock/settings.py: 현재 Django 프로젝트의 환경 및 구성을 저장합니다. Django settings에서 환경 설정이 어떻게 동작하는지 확인할 수 있습니다.
   5. django_stock/urls.py: 현재 Django project 의 URL 선언을 저장합니다. Django 로 작성된 사이트의 “목차” 라고 할 수 있습니다. URL dispatcher 에서 URL 에 대한 자세한 내용을 읽어보세요.
   6. django_stock/asgi.py: 현재 프로젝트를 서비스하기 위한 ASGI-호환 웹 서버의 진입점입니다. 자세한 내용은 ASGI를 사용하여 배포하는 방법 를 참조하십시오.
   7. django_stock/wsgi.py: 현재 프로젝트를 서비스하기 위한 WSGI 호환 웹 서버의 진입점입니다. WSGI를 사용하여 배포하는 방법를 읽어보세요.

4. 실행
    ```bash
            $ python manage.py runserver
    ```  
   실행 후 http://127.0.0.1:8000/ 에 접속하면 나온다.

## [tutorial](https://docs.djangoproject.com/ko/4.1/intro/tutorial01/) 에 있는 동작 수행

1. 앱 생성
    ```bash
            $ python manage.py startapp polls
    ```

2. view 작성하기
   polls view에 아래와 같이 작성한다.
    ```python
            from django.http import HttpResponse

            def index(request):
                return HttpResponse("Hello, world. You're at the polls index.")
    ```
   
    Django에서의 view MVC 에서 controller 와 비슷한 역활을 한다. 데이터를 http response로 보낸다


3. DB 연결
   1. django_stock/settings.py 에서 DATABASES 부분을 수정한다.
        ```python
                DATABASES = {
                    'default': {
                        'ENGINE': 'django.db.backends.sqlite3',
                        'NAME': BASE_DIR / 'db.sqlite3',
                    }
                }
        ```  
   
   2. django에서 필요한DB 생성 DB 생성
        ```bash
                $ python manage.py migrate
        ```
      
4. model 만들기  
   polls의 model을 수정해서 만들어준 다음 하기 명령어를 입력한다.  
    ```bash
              $ python manage.py makemigrations polls
    ```  
    ```bash
              $ python manage.py sqlmigrate polls 0001
    ```  
    ```bash
              $ python manage.py migrate
    ```  

    해당 과정을 모두 수행하면  localhost 에 DB가 생성 된다.  
  

5. 관리자 생성하기  
   관리자 사이트에 로그인 할수 있는 사용자를 생성합니다.  
    ```bash
              $ python manage.py createsuperuser
    ```  
    ```bash
              Username (leave blank to use 'user'): admin
              Email address: admin@example.com
    ```  
   이후에 http://127.0.0.1:8000/admin/ 로 접속하면 DB 변경 가능한 관리자 화면 생성 가능
  
  
6. view에 model 연결하기  
   step 1 ) view 로 인자를 받을 수 있도록 샘플 views.py와 urls.py에 추가 한다.
   step 2 ) model과 view 연결
   step 3 ) 화면에서 보이게 한다.
