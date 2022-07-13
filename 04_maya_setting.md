

## [Centos : Maya 환경 구성]


#### 채크 사항
- Maya.env 에 PYTHONPATH 변수 추가해서, sys.path 에 들어갈 경로를 미리 지정
-- 위치 : /home/{user_name}/maya/{maya_version}
-- 참고자료 : https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2018/ENU/Maya-EnvVar/files/GUID-8EFB1AC1-ED7D-4099-9EEE-624097872C04-htm.html

- Maya startup script : 
-- 위치 : /home/{user_name}/maya/scripts

- Start up shelf : 
-- 위치 : /home/{user_name}/maya/{maya_version}/prefs/shelves

- hostname : 툴 실행시, shotgun_api3 사용 기준이 hostname 이다보니, 윈도우의 hostname과 동일해야함
