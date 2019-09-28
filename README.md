# P1. django

**프로젝트 파일 명
- Django 에서 사용중인 이름 피한다. 
파일 위치
DocumentFoot에 코드가 함께존재하는 것은 피하고 바깥에 둔다.
>보안상 문제때문이다.

cmd 창에서 파이썬 manage 파일명  runserver 포트번호 

**startproject
startapp
앱:특정 기능 수행하는 웹어플리케이션
프로젝트: 이런 앱들과 설정 묶어놓은 것

**include() : url 같은 시점까지 잘라내고 남은 부분 후속처리>나머지 부분 URLconf로 전달
다른 url 패턴을 포함할때마다 include() 사용

**path() : html 페이지를 연결해주기 위한 프레임워크 API 함수.
 path(route=route, view=view, kwargs=kwargs, name=name)


1.route > url 패턴 문자열. 일치하는 패턴을 찾으 때 까지 URL 리스트 순서대로 비교
	url path 에 해당
2.view > HttpRequest 객체 첫째 인수로/ 특정한 view 함수 호출 
	보여줄 페이지에 대한 정의
3.kwargs > 임의의 키워드 인수들 view에 사전형으로 전달된다.
	python의 인자처리 정책. args와 비교하여 보면, args는 단순히 입력되는 인자값에 대한 전달만 처리
	kwarg는 인자명 + 인자값을 함께 전달한다.
	json같은 역할을 수행하는 구조체를 통해 원하는 인자 전달 할 수 있도록 설계된 것
4.name > URL 이름 지어 어디에서나 참조 가능. 


ex)
path('polls/<pageName>/', views.reqArchive, {'name':'argv'})
이렇게 전달 된다. views.reqArchive(requtest , pageName, name='argv')



# P2
*database - sqlite 사용할 예정
*DRY 철학 : 반복하지 말것.
*고유한 개념/ 데이터는 단 한 번 단 한 곳에 존재 하도록 한다. 



# P3
> template / polls / index.html 추가

*view 공개 인터페이스
*django는 요청된 URL 조사하여 view 선택 
*URLcongs 사용한다. >URL과 뷰에 연결

/polls/34/ 요청 > ROOT_URLCONF 설정에의해 해당 모듈 바라봄
mysite.urls의 urlpatterns 변수 찾고
polls/ 찾고 남은 텍스트 34/를 전달하고 처리 진행.
> detail() 뷰함수 호출됨.


**템플릿 네임스페이싱 
Django 는 이름이 일치하는 첫번째 템플릿을 선택하므로 
동일한 이름이 다른 어플리케이션에 있으면 구분을 핤없으므로
이름공간으로 구분하게 된다.


**render()
*index() 뷰를 단축기능으로 작성
*render(request 객체 , 템플릿 이름, (선택)context 사전형 객체)


**get_object_or_404() : 객체가 존재하지 않을때 get() 사용하여 예외 발생.
(Django모델을 첫째인자, ) > 객체 존재안하면 Http404예외
유사 함수로
get_list_or_404() 함수 > get대신 filter()쓴다. 리스트 빈경우 Http404 예외발생


# P4


