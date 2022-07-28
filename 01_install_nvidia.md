### 출처 : https://github.com/lazypic/tdcourse/blob/8d99508a02f9dbfd35e0189ff44febd44a89bd5a/docs/install_nvidia.md

# 그래픽카드 드라이버 셋팅



그래픽카드로 현재 사용중인 드라이버를 체크해보겠습니다.

```bash
$ su
#  lshw -numeric -C display
```

driver 부분이 `driver=nouveau` 로 잡혀있는지 체크합니다.

## nouveau란?

nouveau(누브~) 프랑스어로 `처음부터, 새롭게 다시..`라는 뜻을 가진 단어입니다.
[nouveau](https://nouveau.freedesktop.org/wiki/)프로젝트는 NVIDIA 그래픽 카드용 오픈소스 드라이버입니다. 기본적인 리눅스를 사용할 때는 nouveau 드라이버로 충분하지만 전문적인 그래픽작업을 할 때는 그래픽카드의 부가적인 기능들이 필요합니다. 안타깝게도 NVIDIA 드라이버는 폐쇄소스 코드라서 그래픽카드의 부가적인 기능을 사용하기 위해서는 정식 드라이버를 설치해야 한답니다.

> nvidia가 안드로이드등 리눅스 부문에서 돈을 벌면서, 지적재산권 보호를 위해 오픈소스 드라이버를 위한 정보를 제공하지 않는다는 이유 생긴 사소한 사건. - 49분 59초 : https://www.youtube.com/watch?v=MShbP3OpASA

## 설치

그래픽카드 드라이버를 설치하기 위해서는 yum 업데이트 및 아래 도구가 필요합니다.

```bash
$ su
# yum update
# yum install kernel-devel
# yum install kernel-headers
# yum install gcc make
```


```bash
# uname -r
# rpm -q kernel-devel
```

중요 : 위 명령어를 타이핑 했을 때 무조껀 버전이 같아야 합니다.
버전이 같지 않다면 재부팅하고 설치했던것 삭제 이후 아래의 방법으로 진행. 맞을때까지 해야됨

```bash
# 만일 위 버전이 서로 맞지 않을경우 
# yum(또는 dnf) remove kernel-devel
# yum(또는 dnf) remove kernel-headers
# sudo dnf install kernel-devel-$(uname -r) kernel-headers-$(uname -r)
```


강의실 조건에 맞는 드라이버를 다운로드 합니다.
http://www.nvidia.com/drivers
아래의 명령어로 그래픽 드라이버 버전 찾기
```bash
# lshw -numeric -C display
```

```bash
# cd ~/Downloads
```

grub 설정파일이 있는 곳으로 이동후 설정파일을 백업하고 편집합니다.

```bash
# cd /etc/default
# cp grub grub.bak
# vim grub
```

내용 내용처럼 변경합니다. 6번째 줄만 변경해주세요.

```bash
1: GRUB_TIMEOUT=5
2: GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
3: GRUB_DEFAULT=saved
4: GRUB_DISABLE_SUBMENU=true
5: GRUB_TERMINAL_OUTPUT="console"
6: GRUB_CMDLINE_LINUX="crashkernel=auto rhgb quiet nouveau.modeset=0"
7: GRUB_DISABLE_RECOVERY="true"
```

```bash
# grub2-mkconfig -o /boot/grub2/grub.cfg
# grub2-mkconfig -o /boot/efi/EFI/centos/grub.cfg --> centos로 되어있지만 rocky일경우 centos를 rocky로 바꿔서 진행
#    --> grub2-mkconfig -o /boot/efi/EFI/rocky/grub.cfg
```

재부팅합니다.

```bash
# reboot
```

nouveau가 설정되지 않았기 때문에 GNOME 데스크탑 접근시 화면이 깨질 수 있습니다.
화면이 깨진다면 `Ctrl + Alt + F2` 키를 눌러서 콘솔접근을 해주세요.

```bash
#  lshw -numeric -C display
```

`driver=nouveau` 부분이 사라져 있는지 체크합니다.

그래픽카드 드라이버를 설치하기 위해서는 Xorg server를 중지해야합니다.

```bash
# systemctl isolate multi-user.target
```


만일 .run 파일로 설치시 계속 에러가 나올경우
--> 위에서 확인했던 kernel 버전이 맞는지 확인
--> /var/.../~.log내용에서 어떤것이 설치가 안되어있는지등의 메세지를 확인해서 진행
```bash
# cd ~/Downloads
# bash ./NVIDIA-Linux-x86_64-410.78.run   
                      --> 설치도중 에러가 나오면, 안내해주는대로, 
                          /var/log/nvidi~.log 이름의 파일을 찾아 해당 로그를 보고 필요한것을 yum install
# reboot
```

잘 설치가 되었다면 GNOME 데스크탑 터미널에서 아래처럼 타이핑해서 설정창이 잘 뜨는지 체크합니다.

```bash
$ nvidia-settings
```

## Reference

https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-centos-7-linux
