# [centos 기초]


- 만약 외부 서버 경로가 있다면 경로를 mount 하기
	- 비어있는 폴더 만들기 --> 경로들을 연결해서 mount 하기
    - sudo mount -all

- 디렉토리 구조 파악 필요
https://dana-study-log.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%8C%EC%9D%BC-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EA%B5%AC%EC%A1%B0-%EB%A3%A8%ED%8A%B8-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC-%ED%99%88-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC

- sudo mount -all
- python2.7.5


- 단축키들 설정 :
    - open terminal ----------------------> ctrl+shift+enter
    - open Chrome : $ google-chrome ------> ctrl+shift+F1
    - open 메모장  ----------------------------------------------> ctrl+shift+/
    - open nautilus  ----------------------------------------------> ctrl+shift+(+)
    - screen shot ------------------------> ctrl+shift+(*)


- 윈도우 단축키
    - 왼쪽 오른쪽 split view : super(윈도우키) + 좌우 방향키
    - 전체 화면  : super + 위
    - 최소화 화면 : super + 아래
    - 화면 내리기 : super + h








# [셋팅 부분]

- linux 경로를 윈도우 방식 경로 표시하는 방법

    - [ctrl+L와 다른방법 Link](http://choesin.com/ubuntu%EC%9D%98-%ED%8C%8C%EC%9D%BC-%EA%B4%80%EB%A6%AC%EC%9E%90%EC%97%90%EC%84%9C-%EC%9D%B4%EB%8F%99-%EA%B2%BD%EB%A1%9C-%EB%8C%80%EC%8B%A0-%ED%83%90%EC%83%89-%ED%91%9C%EC%8B%9C-%EC%A4%84%EC%9D%84)

- nvidia 그래픽 드라이버 새롭게 연결 필요

    - [how to Link](https://blog.naver.com/jcss456/221328104556)

    ** linux는 기본적으로 nouveau 그래픽 카드 사용








# [ 필수 실행되는 파일들 ]
- .bashrc / .bash_profile / .profile / rc.local / fstab
    #### etc , root , /home/{username} 에 각각 다 있음
    #### 현재로써는 /home/{username} 만을 사용
- .bash_profile : 시스템에 로그인할 때마다 로드됩니다. 
- .bashrc :  이미 로그인 한 상태에서 새 터미널 창을 열 때마다 로드
- .profile







# [필요한 command]

- 기본적인 명령어 모음

    - [명령어 모음 link](https://dana-study-log.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%EB%AA%85%EB%A0%B9%EC%96%B4-%EB%AA%A8%EC%9D%8C#mv)


- 파일 컨트롤
	- sudo rm [파일명] : 삭제
	- cd ~ : 홈 경로로 변경

- sudo mount -all
- gedit [파일명] : 해당 파일을 메모장으로 열기
- wget [인터넷상 파일 주소] : 해당 파일 인터넷에서 다운로드
- sudo yum install [설치파일 이름] : 설치
    - tab
- tar.gz 파일을 통한 설치 (build 가 필요한 경우)
https://www.rosehosting.com/blog/how-to-install-tar-gz-in-centos/


- nautilus [경로] : 해당 경로를 시작으로 파일 탐색기 열기


- 환경 변수 관리
https://sosobaba.tistory.com/279


- 권한 부분
https://recipes4dev.tistory.com/175
chown : 그룹 권한에 대한 면경 : change own 약자


- 설치된것 찾기 경로찾기
https://it-serial.tistory.com/3


- 약자로 등록
alias


- 실행하기 명령어
		- sh filname.sh 을 하게 되면 해당 .sh 파일 실행

		- .sh 파일이 아니면 그냥 해당 파일 명 또는 source filname 으로 실행 가능



- 이제까지 입력했던 로그들
history
ex) history |grep



- 터미널에 있는 출력값들 clipboard에 저장
xclip사용 : .bashrc 또는 .bash_profile 에 alias로 등록해서 사용하는것을 추천

