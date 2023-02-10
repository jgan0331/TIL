### JPA 테스트 프로젝트 생성

https://kim-oriental.tistory.com/20

위 글 따라서 프로젝트 생성해서 사용해보는 중

### 오류
프로젝트 생성 후 Spring Boot 앱으로 실행했을 때 그냥 브라우저로 접속했을 땐 되는데 포스트맨 웹 버전으로는 안됨!

..이라고 쓰고 잠시 뒤에 다시 요청하니까 됐다.
포스트맨 설치를 해서 된건지? 설치를 하니까 프록시 설정이 적용돼서 된건지? 시간이 지나서 된건지..?

### 오류 2
Get 요청시 아래와 같은 오류가 뜬다.

2023-02-10T23:36:39.304+09:00[0;39m [32m INFO[0;39m [35m39600[0;39m [2m---[0;39m [2m[nio-8080-exec-4][0;39m [36morg.apache.tomcat.util.http.Parameters  [0;39m [2m:[0;39m Character decoding failed. Parameter [name] with value [Ann%] has been ignored. Note that the name and value quoted here may be corrupted due to the failed decoding. Use debug level logging to see the original, non-corrupted values.
 Note: further occurrences of Parameter errors will be logged at DEBUG level.

검색해보니 특수문자 인코딩 오류라고 한다.
기본 인코딩 문자가 여러가지 있는데 그 중 %도 포함이 되어 %가 무시되는 현상

서버에서는 파라미터를 인코딩해서 넘겨주는 방식으로 만든다.
포스트맨에서도 따로 설정할 수 있겠지만 테스트니 간단하게 아래 블로그를 참고해서 파라미터를 %에서 %25로 요청해주었다.

https://m.blog.naver.com/csgct/220444910779


 문자

URL 인코딩

문자 

URL 인코딩 

 탭

%09 

? 

%3F 

 공백

%20 

@

%40

 !

 %21

 

%3E

 "

 %22

{

%7B

 #

 %23

}

%7D

 %

 %25

[

%5B

 &

 %26

]

%5D

 (

 %28

`

%60

 )

 %29

|

%7C

 +

 %2B

~

%7E

 \

 %5C

 

 

 ,

 %2C

 

 

 .

 %2E

 

 

 /

 %2F

 

 

 :

 %3A

 

 

 ;

 %3B

 

 

 <

 %3C

 

 

 >

 %3E

 

 

 =

 %3D

 

 

