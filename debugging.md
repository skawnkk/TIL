<h1>debugging</h1>

<br>


<h3>1. breakpoints란</h3>

- __Breakpoint 중단점__<br>
: 소스 코드의 특정 지점에서 디버깅을 목적으로 프로그램의 실행을 멈추는데 사용한다.<br>
  중단점이 실행된 상태에서는 중단된 상태의 영역, 즉 해당 스콥(scope)에 접근할 수 있다.<br>
  콘솔 혹은 디버깅 패널(variables, watch, call stack)을 통해 확인 가능하다.<br>
  
  ex) 디버깅진행: 해당 중지 시점의 변수체크, 명령어 실행<br>


- __사용(삽입/삭제)__<br>
-. vs_code 여백라인 클릭<br>
-. 현재 줄에서 F9으로 선택 가능<br>
-. 디버깅메뉴에서 breakpoint checkbox<br>
-. 해당 라인에 debugger; 입력<br>

- __상태__<br>
-. red_point : 활성화, 해당점에서 실행을 멈춤<br>
-. grey_point : 비활성화<br>
-. conditional breakpoint : 표현식이 참인 경우에만 실행을 중지<br>
-. logpoint(다이아몬드 모양): 실행이 중단되지 않고 콘솔에 메시지를 기록, 중괄호{}안에 평가 표현식을 작성한다.<br><br>



<h3>2. 유용한 debugging tool</h3>
<img src="https://code.visualstudio.com/assets/docs/editor/debugging/debugging_hero.png">

 debug side bar><br>
- __Watch__<br>
: 모든 유효한 자바스크립트 표현식을 + 버튼을 통해 저장<br>
시간에 따른 변수 값을 모니터링 할 수 있다.<br>
(ex- typeof variavle: 변수의 상태에 따라 값을 보여 준다.)<br>

- __call stack__<br>
: breakpoint로 중단된 코드가 실행되게된 경과를 역순으로 보여준다.<br>
 클릭하면 해당 코드로 이동되며 변수들이 새로 재평가 된다.<br>
 
- __scope__<br>
: 현재 정의된 모든 변수들을 나타낸다. (local/global)<br><br>

debug tool button><br>
- __Step over / Step into/ Step out__<br>
: 디버깅 툴 버튼 -> 프로그램 실행을 추적하는 역할을 한다.<br>
-.Resume: 스크립트 실행을 다시 시작함 (단축키 F8)<br>
-.Step: 다음 명령어 실행(비동기 동작 무시__ step into와 차이점 (단축키 F9)<br>
-.Step over: 다음 명령어를 실행하되, 함수 안으로 들어가진 않음 (단축키 F10)<br>
-.Step into: 다음 명령어를 실행<br>
  다음 명령어가 비동기 동작을 담당하는 코드일 경우, 동작이 완료될 때까지 대기<br>
-.Step out: 실행 중인 함수를 종료시킴 (단축키 shift+F11)<br><br>

### 참고사이트
vs_code_debugging: https://code.visualstudio.com/docs/editor/debugging<br>
chrome dev tool: https://developers.google.com/web/tools/chrome-devtools/javascript?hl=ko#watch-expressions<br>
