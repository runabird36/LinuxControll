# [centos(Rocky) 설치]

- 우선 공식 홈페이지에서, os를 usb에 베이크

- 컴퓨터에 usb 연결 후, 부팅 초기에 F8 (아닐 경우 F7~F11다 눌러보기) 눌러서, 설치할 os 설치

- 파티션 설치등 여러가지 셋팅해서 gui 모드로 켜지기까지 하기
    - 파티션
    - 언어
    - 네트워크
    - root / client 계정 생성



- 단축키들 설정 :
    - open terminal : gnome-terminal ----------------------> ctrl+shift+enter
    - open Chrome : $ google-chrome ------> ctrl+shift+F1
    - open 메모장  : gedit ----------------------------------------------> ctrl+shift+/
    - open nautilus : nautilus . ----------------------------------------------> ctrl+shift+(+)
    - screen shot --> save a screenshot of an area to Pictures ------------------------> ctrl+shift+(*)



- 한글 설정 / time zone
    
- vscode / git 설치 
    - vscode : 공식 홈페이지에서 .rpm 파일 받아와서 rpm 명령어로 실행 및 설치
        - python / json / markdown 관련 플러그인 설치
    - git : yum install git


- 그래픽 드라이버를 defautl인 nouveau에서 nvidia 것으로 바꾸기


- 만약 외부 서버 경로가 있다면, lustre관련 기능을 설치 이후, 경로를 mount 하기
	- 비어있는 폴더 만들기 --> 경로들을 연결해서 mount 하기
    - sudo mount -all

- 디렉토리 구조 파악 필요
https://dana-study-log.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%8C%EC%9D%BC-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EA%B5%AC%EC%A1%B0-%EB%A3%A8%ED%8A%B8-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC-%ED%99%88-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC

- sudo mount -all


- python 이 default 로 3.6이 깔려있는데, 모든 파이썬 삭제이후, 필요한 버전으로 셋팅
- python2.7.5



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
    - [tdcourse의 how to](https://github.com/lazypic/tdcourse/blob/8d99508a02f9dbfd35e0189ff44febd44a89bd5a/docs/install_nvidia.md)
    - [rocky 하면서 반영한 내것 how to](https://github.com/runabird36/LinuxControll/blob/main/01_install_nvidia.md)

    ** linux는 기본적으로 nouveau 그래픽 카드 사용


- [lustre 설치 방법](https://docs.aws.amazon.com/ko_kr/fsx/latest/LustreGuide/install-lustre-client.html)


- 경로 / 환경변수 / lustre / repository 등 환경 구성을 어떻게 할지 설계
    







# [경로]
- 윈도우에서는 바탕화면, 내문서, 다운로드등의 폴더들이 있는 경로
    ```
    # ~ 하고 동일 
    /home/tiayeong.song
    ```
- 윈도우에서는 .exe 파일들이 있는 경로
    ```
    /bin
    /usr/bin
    ```
    
- 윈도우에서는 설치했을때 필요한 모든 파일들을 넣어두는 경로
    ```
    /lib        /lib64
    /usr/lib    /usr/lib64
    ```
    ** 리눅스에서는 .run / .rpm / .tar.gz 으로 설치시 알아서 bin 과 lib 으로 나누어서 들어가는듯



# [ 필수 실행되는 파일들 ]
- .bashrc / .bash_profile / .profile / rc.local / fstab
    #### etc , root , /home/{username} 에 각각 다 있음
    #### 현재로써는 /home/{username} 만을 사용
- .bash_profile : 시스템에 로그인할 때마다 로드됩니다. 
- .bashrc :  이미 로그인 한 상태에서 새 터미널 창을 열 때마다 로드
- .profile




# [설치 및 삭제]
- ### [How to](https://conory.com/blog/42585)
- 자체 소스파일 컴파일로 설치
    - https://www.rosehosting.com/blog/how-to-install-tar-gz-in-centos/
- 패키지 방식 설치
    - 패키지 설치 확인 : 
    ```
    rpm -qa | grep -i [패키지 이름] # 대소문자 구분없이 확인
    ```
    - 패키지 설치
    ```
    rpm -Uvh [패키지 이름]
    ```
    - 패키지 제거
    ```
    rpm -ev [패키지 이름]
    ```
- 저장소를 통한 자동 설치 도구 이용 == dnf (최신버전)
    - 레드헷 계열 (Red Hat/Centos/Fedora)
    ```
    sudo yum install [패키지 이름] + tab (tab을 추가하게 되면 해당 이름을 갖고있는 모든 패키지 검색)
    ```

- ### 삭제의 경우, 삭제 방식이 명시되어있지 않을경우, 모든 파일 및 폴더를 찾아 삭제



# [필요한 command]

- 기본적인 명령어 모음

    - [명령어 모음 link](https://dana-study-log.tistory.com/entry/Linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%EB%AA%85%EB%A0%B9%EC%96%B4-%EB%AA%A8%EC%9D%8C#mv)

    - Manual
        - 사용방법 확인 명령
            ```
            man {command}
           ```
        - ```
            clear
            ```
    - Navigating file system
        - 현재 경로 확인 및 출력
            ```
            pwd
            ```
        - 해당 경로를 탐색기로 열기
            ```
            nautilus {주소}
            ```
        - 현재 경로의 파일, 폴더 list up + long name (-l) + 숨김파일 포함 (-a)
            ```
            ls -la
            ```
        - 지정한 경로에서 찾고자 하는 이름을 갖고있는 파일 또는 폴더 찾기
            ```
            find {dir} -type file -name "*.txt"
            find {dir} -type directory -name "*2"
            ```
        - 설치된 bin 실행 파일 찾기
            ```
            which atom
            ```
    - Create and Manage files
        - 파일 생성
            ```
            touch {이름}
            ```
        - 해당 파일의 내용물 출력
            ```
            cat {파일명}
            ```
        - 재출력
            ```
            echo $MAIL
            ```
        - 파이프 : 명령과 명령을 이어줌으로써, 앞의 명령의 얻어지는 결과물을 뒷 명령어에 전달하는 행동
            ```
            ls -la |grep -i "python" 
            
            # 현재 경로에서 우선 파일, 폴더 listup 그리고 그 결과물 중에서 python 이라는 이름을 갖고있는 파일 또는 폴더 찾기 (대소문자 상관 없이)
            ```
        - 리다이렉트 : 표준 입출력의 방향 또는 위치를 바꾸는 행동
            ```
            ls -la > sample.txt 
            # ls -la 명령어의 결과물을 sample.txt 파일에 입력 및 저장
            ```
        - 폴더 생성 / 복사 / 이동 / 삭제
            ```
            - mkdir
            - cp {file} {to_dir}
            - mv {file} {to_dir}
            - rm -r {dir} # 해당 경로내의 모든 폴더 및 파일 삭제
            ```
        - 글자 찾기
            ```
            --> ll |grep
            --> grep -n "world" *.txt : 라인수 같이 출력
            --> grep -ni "world" *.txt : 라인수 같이 + 대소문자 상관없이
            --> grep -nir "world" *.txt : 라인수 같이 + 대소문자 상관없이 + 해당 경로안의 모든 폴더의 모든 파일 대상
            ```
    - Work with environment variables
        - 환경 변수 지정
            ```
            export {변수명}="{값}"
            ```
        - [환경변수 관리](https://sosobaba.tistory.com/279)



- sudo mount -all
- gedit [파일명] : 해당 파일을 메모장으로 열기
- wget [인터넷상 파일 주소] : 해당 파일 인터넷에서 다운로드
- sudo yum install [설치파일 이름] : 설치
    - tab
- tar.gz 파일을 통한 설치 (build 가 필요한 경우)
https://www.rosehosting.com/blog/how-to-install-tar-gz-in-centos/


- 권한 부분
https://recipes4dev.tistory.com/175
chown : 그룹 권한에 대한 면경 : change own 약자


- 설치된것 찾기 경로찾기
https://it-serial.tistory.com/3


- 약자로 등록
    ``` 
    alias
    ```


- 실행하기 명령어
		- sh filname.sh 을 하게 되면 해당 .sh 파일 실행

		- .sh 파일이 아니면 그냥 해당 파일 명 또는 source filname 으로 실행 가능



- 이제까지 입력했던 로그들
    ```
    history
    ex) history |grep
    ```


- 터미널에 있는 출력값들 clipboard에 저장
    - xclip사용 : .bashrc 또는 .bash_profile 에 alias로 등록해서 사용하는것을 추천
        ```
        alias cc="xargs echo -n | xclip -selection clipboard"
        alias vv="xclip -o selection clipboard"
        ```

- crontab
    - 정의 : 윈도우의 스케줄러 같은 기능
    - [How to](https://www.lesstif.com/lpt/linux-scheduler-crontab-77955238.html)
    - [시간 표현](https://crontab.guru/)
    - 지정된 crontab list up
    ```
    crontab -l
    ```
    - crontab edit
    ```
    crontab -e
    ```
- rsync : 동기화 기능
    - [How to](https://www.manualfactory.net/10204)
    ```
    rsync -avz --exclude '.git' --exclude '.gitmessage' --delete /usersetup/pipeline/users/taiyeong/linux/Documents/ /home/taiyeong.song/Documents/my_git/LinuxControll
    ```

