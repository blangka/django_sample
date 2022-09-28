# django_basic

django의 기본 적인 구조에 대해서 알아 보는 프로젝트로 시작합니다.  
간단하게 [주식 검색 웹 만들기](https://hmg.udemy.com/course/django-s/learn/lecture/18126411#overview) 강의를 보며 프로젝트를 구성할 예정입니다.  
공식문서로는 [django doc](https://docs.djangoproject.com/ko/4.1/intro/overview) 을 참고하여 기본 구조 및 상세 내용을 프로젝트 진행 하면서 기재할 예정입니다.

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