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

<h5>01. Virtual Box설치</h5>
[주소에 대한 설명](http://www.google.co.kr)

가상머신: 하드웨어를 소프트웨어적으로 구현해서 그 위에 운영체제가 작동하도록 하는 기술.  

- 다른 운영체제를 사용해야 하는 경우(맥OS에서 윈도우, 윈도우에서 리눅스)  
- 독립된 작업공간이 필요한 경우 (바이러스 회피, 백업)  
- 하나의 머신에서 여러명에게 운영체제 환경을 제공할 때 필요합니다.  

<br>
<h5>02. Ubuntu 설치(Desktop/ server)</h5>

새로만들기 기본 설정이 마치고 나면  
저장소 설정: [설정]-[저장소]-[광학 드라이브]에 우분투에서 다운받았던 이미지를 넣어줍니다    
네트워크 설정: [설정]-[네트워크]-[고급]-[포트설정: 22(ssh), 80(브라우저)추가]  

설치 후 작업   
<pre>
dpkg -l | grep ssh -> (openssh-server가 있는지 체크_내가 작업을 할 수 있는지)
=>없다면 설치: sudo apt -y install openssh-server
</pre>

<pre>
ps -ef | grep ssh
:sshd-D [listener] __ssh가 잘 실행되고 있음을 보여줌</pre>

네트워크 설정
<pre>
systemctl stop ufw (방화벽)
systemcl disable ufw
systemctl start ssh (설치)
cmd ipconfig 네트워크IPv4주소로 바꿔서 다시 해보기
((cmd ssh k@192.168.56.1))
putty ip주소 위에걸로
</pre>

<br>
<h5>03. ssh client_ puTTy설치</h5>
SSH: Secure Sell의 약자로 원격지에 있는 컴퓨터를 안전하게 제어하기 위한 프로토콜 또는 이 프로토콜을 사용하는 프로그램들을 의미합니다.  
현재 사용하고있는 PC가 SSH 클라이언트로, 설치하려는 리눅스가 SSH 서버의 관계로 상호작용하면서 리눅스 운영체제를 제어합니다.  
리눅스와 Mac과 같은 Unix 계열의 운영체제는 기본적으로 SSH 클라이언트가 설치 되어 있으나 윈도우 운영체제에는 SSH 클라이언트가 설치되어 있지 않습니다  
때문에 윈도우에서는 Unix계열의 운영체제를 제어하기 위해 puTTY, Xshell에서 ssh를 설치받아야 합니다.

<h1>쉘 스크립트 작성</h1>
<h3>01. 파일 및 폴더 생성</h3>

<pre><code>#!/bin/sh
echo "1.making new directory"
for i in {1..16}
do
        mkdir day$i
done</code></pre>


<pre><code>
#!/bin/bash
for i in {1,3,5,7,9}
do
        touch a.cs
        mv a.cs day$i
done
</code></pre>

<h3>02. 파일 분류 & 집!</h3>
<pre><code>
#!/bin/sh
echo "distling"
if [ -d backup ]; then
        rm -rf backup
fi
mkdir backup
for i in {1..16}
do
        if [ -f day$i/a.cs ]; then
                cp day$i/a.cs backup/$i.cs
        else
                echo "day$i is empty"
        fi
done
NAME=$(date +%Y%m%d)
zip -r "$NAME".zip ./backup/*
scp "$NAME".zip k@192.168.56.1:/backup

</code></pre>

[결과] tree구조를 보면된다.  

(*tree는 윈도우 터미널에서는 사용할 수 없기 때문에 따로 설치하여야 한다.)    
총 16개의 day폴더가 생성되었고  
지정한 1,3,5,7,9day 폴더안에 a.cs파일이 담겨있다.  
또 backup파일에 a.cs파일이 담겨있던 폴더명을 가진 *.cs파일이 저장되었다.  
오늘날짜를 파일명으로한 압축파일도 생성완료!  
![success](https://blogfiles.pstatic.net/MjAyMTAxMDlfMTI0/MDAxNjEwMTMyMDc5OTU0.ivuruXJXtcg5an63GVC0zvAYiarXw305ngsiWZhW4Lsg.4Vzu93a1TXUQv7qN0smBMqXOcE4hjfmGrFHWjkcTmykg.PNG.namju1v/SE-f8846f2d-ecc6-4f41-9bf5-8b96ed225cb0.png)

그치만 내 가상환경으로 파일을 보내주는 작업은  실패했다.  
이유는 아직 모르겠다...  
가상환경이랑 연결은 되어있는데... 물어봐야죠..  
(가상환경에 로그인되었고... '음 맛있다'라는 echo설정한게 출력된걸보니..)  

![fail](https://blogfiles.pstatic.net/MjAyMTAxMDlfNTcg/MDAxNjEwMTMyMTI4MjUw.9T2Lic8F3jR0yXVXgaUzBO3Vb9OqVB5gKU_vIQPPs48g.VqgsZOxgkBFWTAmDaquN_9kBj6MOOEvCVJJ51W5Xnr8g.PNG.namju1v/SE-20e9690a-ca6e-4894-995c-ae46d49dbba1.png)
