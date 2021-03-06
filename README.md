# 웹이라는 개념에서 탈출한 JavaScript ==> Node.js<br>
## 생활코딩님의 강의를 참고하였습니다.

#### 초기상태
![image](https://user-images.githubusercontent.com/60773356/108064584-3f0fa400-70a0-11eb-97b1-b46a652f88bd.png)
![image](https://user-images.githubusercontent.com/60773356/108064674-5a7aaf00-70a0-11eb-9985-8f285815efbf.png)
* CSS
* HTML
* JavaScript


#### create 버튼 클릭
![image](https://user-images.githubusercontent.com/60773356/108064857-96ae0f80-70a0-11eb-9ef8-cebbdd8303fe.png)
* 새로운 문서를 작성 후, 제출
![image](https://user-images.githubusercontent.com/60773356/108064989-bfcea000-70a0-11eb-98e5-d584ffdab398.png)

#### 새로운 문서 작성
![image](https://user-images.githubusercontent.com/60773356/108065066-d2e17000-70a0-11eb-890a-a7fa0d932016.png)
![image](https://user-images.githubusercontent.com/60773356/108065150-eab8f400-70a0-11eb-8843-ae1296d5ab24.png)
* Visual Code내에서도 문서가 자동으로 생성된 것을 확인할 수 있다.
* **Delete, Update 또한 마찬가지로 정상 작동**




---
### 수업 내용 필기
```
20/12/29 생활코딩 node.js 수업 시작

//fs.readFileSync node.js의 기능으로 읽어옴.
node.js는 웹서버의 기능도 내장하고 있다.
literal은 정보를 표현하는 방법

templete literals의 시작과 끝을 의미하는 `
이것을 사용하면 원래 문자열을 할때처럼 "문자열" + 변수 + "문자열"
이렇게 하지않고
`문자열 ~~~~ ${변수} ~~~~~ ' 를 하면된다.
중간에 줄바꿈도 \n을 하지않고 그냥 엔터하고 다음줄부터 쓰면되는것.

현재는 각각의 html을 작성하고 main.js를 통해 불러온 것 뿐.
따라서 정적인 각각의 html를 여러개 저장해야함.

http://opentutorials.org:3000/main?id=HTML&page=12를 예시로 보면
http ==> protocol
opentutorials.org ==> host(domain)
3000 ==> port
main ==> path
id=HTML&page=12 ==> query string

이 query string의 값을 바꿔서 홈페이지 변경 가능. 시작은 ?로 시작
이를 통하여 정적인 html이 아닌 node.js로 동적으로 생성한 정보를 
웹에 전달.

CRUD
C - Create
R - Read
U - Update
D - Delete

fs.~~~ ==> fs는 File System

cmd 창에서 cd ..을 입력하면 부모 directory로 이동함.

현재와 같이 본문의 내용을 따로 data폴더에 저장한 후
fs.readefile을 통해 main.js에서 읽어오는 형식으로 실행한다면
data폴더의 본문내용을 수정하는 것은 새로고침을 통해
변경 사항을 확인가능하다.
하지만 main.js를 변경하려면 node.js를 껐다 켜야함.


------------------20/12/30 node.js study


pathname은 쿼리스트링을 제외한 path만을 보여줌
이를통하여 root로 접속했는지를 판별할 수 있다.
즉 우리가 만든 웹페이지인 root로 접속하면 원래대로 화면 보여주고
그 외의 path로 접속하면 에러메세지

fs.readdir은 특정 디렉토리에 있는 목록을 배열에 담아서 
보여준다.
즉 이를 반복문을 통하여 수정,삽입을 한다면 main.js에서 일일이
수정이 필요없이 한번에 모든 내용을 수정가능.

템플릿과 readdir, readfile을 이용하여 node.js를 통하여 페이지를 구성한다면
우리가 data폴더에 문서를 작성하는 것만으로도 목록에 자동으로
추가되고 페이지가 연동된다 ==> 동적인 웹페이지

synchronous & assynchronous (동기적 & 비동기적)
동기적: 어떤 일을 처리한다면 순차적으로 하나를 끝낸 다음에
          그 다음 작업을 수행

비동기적: 어떤 일을 시작한 후 그 일이 끝날 동안 다른 일을
             병렬적으로 수행(동시에 여러가지 처리)
node.js ==> 비동기적인 처리를 위한 여러 기능을 가지고 있음.
하지만 비동기적 처리는 효율적이지만, 굉장히 까다롭고 복잡함.
readFileSync ==> 동기적 처리
==> 리턴 값이 있어서 변수에 값을 담을 수 있음.



readFile ==> 비동기적 처리
매개변수로 callback을 줘야함으로 function즉 함수를 줌.
변수에 값을 담아 사용 x

결론: 동기적 처리를 하면 문장 순서에 따라 값이 출력되지만
비동기적 처리는 먼저 완료된 순서대로 출력된다.
==>syntax/sync.js 코드 참조.


Package Manager
-NPM


input을 통해 내용입력하고 그것을 html form태그로 감싼후,
form태그의 속성인 action에 url을 입력하면 input태그의 속성과 요소의
값을 url에 추가하여 보내줄 수 있다. querystring을 만들어줌.

웹페이지주소를 전달할 때는 수정,삽입,삭제와 같은 기능을 할 수 있는
페이지의 주소는 다른사람이 볼 수 없게 전달해야함.
볼 수 있다면 외부인이 접속하여 수정,삽입,삭제가 가능하므로 보안상 문제
==>정보은닉
==>form태그 속성에 method="post"를 추가하면 보이지 않게 전달
      querystring은 보이지 않고 action값만 보임

웹페이지를 가져올 때는 method="get"
post 방식으로 전달했을 때 컨트롤+쉬프트+i 를 통해 개발자 탭에 
들어가서 네트워크의 headers를 보면 전달된 데이터를 볼 수 있음.

request.on ==> post방식으로 데이터를 전송할 때 받는 메소드  
콜백함수를 통하여 전송받은 데이터를 실행
request.on('data', function(data){}); 'data'를 받음
request.on('end', function(data){}); 더이상 받을 데이터가 없으면 실행
데이터를 받은 후 qs.parse메소드를 통하여 불러옴
==> 즉, 받은 데이터를 객체화 할 수 있다.


--------------20/12/31

fs.writeFile을 통해 동적으로 웹페이지에서 제어
리다이렉션: 사용자가 어떤 페이지에서 처리를 한다음 다른 페이지로
                보내는 것.
writeHead(200) ==> 성공했다는 뜻
writeHead(302) ==> 페이지를 다른페이지로 리다이렉션 시키라는뜻
delete도 링크로 하면 절대 안된다. 보안 ==> post방식
구글 캐싱사건 참고

자바스크립트에서 
roles라는 객체가 있을때
for var i in roles 라는 문장은
for문을 돌면서 i에 roles 객체의 키값이 들어간다.
함수를 변수에 담을 수 있다. (함수==>값)
따라서, 배열이나 객체에 함수를 담아서 사용가능.

동작방법은 그대로 두면서 내부의 코드를 더 효율적으로 바꾸는 행위
==>Refactoring(리팩토링)



pm2 start main.js --watch --ignore-watch="data/*"


----------21/1/1------------------

Module (모듈)
객체를 포함하는 더 큰 개념

특정 객체를 변수에 담고 module.exports를 통해 내보낸다.
그 후 다른 파일에서 require('파일경로+파일명')을 새 변수에 담아.
다른 파일에 있는 객체를 import한 것처럼 사용할 수 있다.

보안
readFile의 경로명을 data/${queryData.id}와 같이 지정해놓으면
..등의 상위디렉토리로 가는 것을 막을 수 없기 때문에
보안상의 심각한 문제가 발생한다.
require('path')를 통하여 필터를 하여 넣어주는것이 안전

사용자가 입력한 정보를 출력할 때에도 보안과정이 필요하다.
예를 들어 create를 할때 본문 내용에
<script></script>태그를 사용하여 한 사용자가 웹페이지를 공격할 수도
있기 때문에 '<', '>'와 같은 특수기호를 문자 그대로 출력하게하는 등
의 방법이 필요.
==> sanitized 모듈을 가져와서 쓰면 편리하게 걸러낼수 있다.



API ( Application Programming Interface)

node.js awesome!
어떤 모듈들이 있는지 알고 이를 사용할 수 있는 것이 실력이고
능력이다.

```












