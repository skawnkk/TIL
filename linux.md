<h1>Linux®</h1>
컴퓨터를 제어할 수 있는 운영체제(Operating System, OS) 중 하나로 오픈소스, 무료사용이 가능한 운영체제 입니다.  
OS는 애플리케이션과 하드웨어 사이에서 모든 소프트웨어와 작업을 수행하는 물리적 리소스를 연결합니다.  
1991년 리누스 토르발스가 미닉스 OS를 사용하는 컴퓨터에서 작업하여 만들어졌고. 커널*에 여러 기능을 지속적 추가하였고 무료 운영체제로 오픈됬습니다.   
GPL라이선스 선택, 소스코드 공개, 공개적 개발모델을 선택한 것이 빠른 성장세를 만들어냈습니다.  
거기에 자체 커널 개발에 난항을 겪던 GNU 프로젝트가 리눅스 컨널에 관심을 가지며 리눅스 커널과 GNU유틸리티가 결합하면서 완전한 운영체제로 거듭나게 됬습니다.  
<br>
UNIX 운영 체제는 주로 모든 사람을 위해 설계된 OSX를 제외한 메인 프레임, 서버 및 워크 스테이션 용으로 개발되었습니다.  
주로 대학, 기업, 대기업 등에서 많이 사용됩니다. 유닉스와의 차이로 리눅스는 데스크톱/랩톱 용도 뿐만 아니라  
웹서버, 클라우드, 안드로이드 및 포터블 게이밍 콘솔 등의 모바일 기기, 각종 임베디드 기기 등을 구동하는 운영체제로 널리 쓰입니다.  
<br>
(*커널 모드 (kernel mode by OS): 특권 명령어 실행과 원하는 작업 수행을 위한 자원 접근을 가능케 하는 모드)


<h3>윈도우에서 리눅스 설치하기

<h4>01. Virtual Box설치</h4>
🔽 http://www.virtualbox.org
가상머신: 하드웨어를 소프트웨어적으로 구현해서 그 위에 운영체제가 작동하도록 하는 기술.  

- 다른 운영체제를 사용해야 하는 경우(맥OS에서 윈도우, 윈도우에서 리눅스)  
- 독립된 작업공간이 필요한 경우 (바이러스 회피, 백업)  
- 하나의 머신에서 여러명에게 운영체제 환경을 제공할 때 필요합니다.  

<br>
<h4>02. Ubuntu 설치(Desktop/ server)</h4>
🔽 https://ubuntu.com/download/desktop  

![vb](https://blogfiles.pstatic.net/MjAyMTAxMDdfMjQz/MDAxNjEwMDI2NjYwODYz.ul4ZRKtvixBdq3768ZO50agU_UOLN35rfVEOhmbIuQ8g.sWo--dQk9-xkRQFZLVkKhcBx1PR3NxxCXhp4mFceLEkg.PNG.namju1v/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2021-01-07_223712.png)

새로만들기 기본 설정(사용자 및 우분투 이름설정)이 마치고 나면  
저장소 설정: [설정]-[저장소]-[광학 드라이브]에 우분투에서 다운받았던 이미지를 넣어줍니다    
네트워크 설정: [설정]-[네트워크]-[고급]-[포트설정: 22(ssh), 80(브라우저)추가]  

![network](https://blogfiles.pstatic.net/MjAyMTAxMDdfNzMg/MDAxNjEwMDI3MjcxMzQ5.Yw-Mt1mM7H6S1ONcwZ1Oy7OIvXt2B_5q-b3qsTUbtzkg.x6Q2LlM4EAXstE0LVHHY_3A28Q-Srvj2bZIjA-Tgms8g.PNG.namju1v/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2021-01-07_224524.png)

![network2](https://postfiles.pstatic.net/MjAyMTAxMDdfNDcg/MDAxNjEwMDI3MjcxMzU1.rWla_2w90IYvfrDz6Flu9Rwdkj8RHgyOuosFmohxHXMg.MxjEiTubGDhGZGHlGWXJp3o_kBE3fcWNXPe90JUPZt8g.PNG.namju1v/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2021-01-07_224638.png?type=w966)

![port](https://blogfiles.pstatic.net/MjAyMTAxMDdfMTM0/MDAxNjEwMDI3MzM2OTI1.X0HMl7PC_V2IvE70pTri6x8t5oxnEEnEi-KVEQW7A4gg.FUw4UjHe3qTCPyh9T8_UZ166u9YxJjieBMKr_eDzo84g.PNG.namju1v/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2021-01-07_224701.png)

<h5>설치 후 작업  </h5> 
<pre>
dpkg -l | grep ssh -> (openssh-server가 있는지 체크_내가 작업을 할 수 있는지)
=>없다면 설치: sudo apt -y install openssh-server
</pre>

![ssh1](https://blogfiles.pstatic.net/MjAyMTAxMDhfNDgg/MDAxNjEwMTE3NTk3MTA0.Dx6xGeUWtCBZVLA3ncp0RiqpVKy8BRZ4gu0dx5XRKGkg.JxCqqHddW7yqLmUFmslm3sHAOt54qRFndjEla57svVAg.PNG.namju1v/SE-20a5fe14-6282-4562-8c2f-4780115bc39e.png)

<pre>
ps -ef | grep ssh
:sshd-D [listener] __ssh가 잘 실행되고 있음을 보여줌</pre>

![ssh2](https://blogfiles.pstatic.net/MjAyMTAxMDhfMjIx/MDAxNjEwMTE3Njk1NDE4.Z_tpdqDpXbLogAGQt5h0yGC03ohnjat_1XdygIsnVRkg.sSQTr7ulidJ05dDLUtZYhSdjVi6vtQSglxTvubDq6f0g.PNG.namju1v/SE-d4e7ca5e-56b2-491d-8983-2e793e0620d2.png)


<h5>네트워크 설정 및 푸티 네트워크 연결오류 해결</h5>

버츄얼 박스 포트포워딩을 다시 작성한다.  
터미널창에 ifconfig입력하여 네트워크 상태를 체크해본다.   
호스트 IP에 127.**,  게스트IP에 10.02.**을 입력한다. (그럼 보통 된다.)  

![setting](https://blogfiles.pstatic.net/MjAyMTAxMDhfMTkg/MDAxNjEwMTE3OTUwNDAz.7qMfgZLP6-JawCc9-EpZ_lzLypYfSwxGG52Oq-nW7M0g.rLZxl6tGahpVhCDQZGNZz6i-_wiKoEP77rTC_f4NiQQg.PNG.namju1v/image.png)

그래도 오류가 난다면 하단 명령어 입력하기
(될때까지 순서대로 실행해보기)

<pre>
systemctl stop ufw (방화벽)
systemcl disable ufw
systemctl start ssh (설치)
cmd ipconfig 네트워크IPv4주소로 바꿔서 다시 해보기
((cmd ssh k@192.168.56.1))
putty ip주소 위에걸로
</pre>

![solved](https://blogfiles.pstatic.net/MjAyMTAxMDlfMjkw/MDAxNjEwMTE4MjQ5NTgy.yEsHJM9SljXI3nZlnkna8LxEotp7bS_GtCwsKPDo5q0g.tuausr6NmstsES53BQfWfO4MPOiz8vLjEdoLMdvoLlwg.PNG.namju1v/image.png)

<br>
<h5>03. ssh client_ puTTy설치</h5>
SSH: Secure Sell의 약자로 원격지에 있는 컴퓨터를 안전하게 제어하기 위한 프로토콜 또는 이 프로토콜을 사용하는 프로그램들을 의미합니다.  
현재 사용하고있는 PC가 SSH 클라이언트로, 설치하려는 리눅스가 SSH 서버의 관계로 상호작용하면서 리눅스 운영체제를 제어합니다.  
리눅스와 Mac과 같은 Unix 계열의 운영체제는 기본적으로 SSH 클라이언트가 설치 되어 있으나 윈도우 운영체제에는 SSH 클라이언트가 설치되어 있지 않습니다  
때문에 윈도우에서는 Unix계열의 운영체제를 제어하기 위해 puTTY, Xshell에서 ssh를 설치받아야 합니다.

<h5>puTTY 사용해보기</H5>
-입력해볼 명령어
- WHO
- WHOAMI
- DATE

DATE를 입력해보니 현재시간과 다르다.
시간이 UTC기준으로 설정되어있어 KST로 바꾸어주는 작업을 한다.  
<PRE><CODE>
  sudo timedatectl set-timezone "Asia/Seoul"
</CODE></PRE>

![DATE](https://blogfiles.pstatic.net/MjAyMTAxMDlfMTUy/MDAxNjEwMTIyMjc5NDU1.HdYUHOyB6NpkEOP_WRvopLhFJA0u405NK6QKENuEHwIg.ww4WVpY3o0IaKuc1_9BeSnV-Y20UK6e-gpDlt1-_85gg.PNG.namju1v/SE-e7759172-11a7-4b1f-bc5c-9b66160b6e97.png)


