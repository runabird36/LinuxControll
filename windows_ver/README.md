

# [셋팅 부분]

    
- 단축키 설정 : 바로가기로 들어가서, 우클릭 + 설정에서 단축키 부분에 입력할 단축키 입력
    - open directory : 윈도우+E (이 기능은 별도의 단축키 설정 불가능)
    - open terminal : ctrl + shift + \
    - open text editor : ctrl + shift + /
    - save a screenshot of an area to Pictures




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
            pwd (powershell) 
            cd (prompt)
            ```
        - 해당 경로를 탐색기로 열기
            ```
            start {주소}
            ```
        - 현재 경로의 파일, 폴더 list up + long name (-l) + 숨김파일 포함 (-a)
            ```
            dir
            ```
        - 지정한 경로에서 찾고자 하는 이름을 갖고있는 파일 또는 폴더 찾기
            ```
            ```
        - 설치된 bin 실행 파일 찾기
            ```
            ```
    - Create and Manage files
        - 파일 생성
            ```
            ```
        - 해당 파일의 내용물 출력
            ```
            ```
        - 재출력
            ```
            echo %MAIL%
            ```
        - 파이프 : 명령과 명령을 이어줌으로써, 앞의 명령의 얻어지는 결과물을 뒷 명령어에 전달하는 행동
            ```
            dir |find-string -i "python" 
            
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
    - clip / Get-clipboard
        ```
        cd |clip  (prompt)
        split-path cd |clip (poweshell)
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

