# CentOS 7�ւ̈ڍs
## CentOS 7�ւ̈ڍs
�{���ȏ��ł�CentOS 6���g���ĉ�������Ă��܂������A���݂ł͐V�����o�[�W�����ł���CentOS 7�������[�X����Ă��܂��B

CentOS 7�ւ̃o�[�W�����A�b�v�����{�I�ȉ^�p�Ǘ��̒m���͑傫���͕ς��܂��񂪁ACentOS 7�ő傫���ύX�ɂȂ����ȉ��̓_�ɂ��ĉ�����܂��B

* SysV init����systemd�ւ̈ڍs
* journald�ɂ�郍�O�L�^
* firewalld�ɂ��p�P�b�g�t�B���^�����O

�܂��A�ύX���ꂽ�킯�ł͂���܂��񂪁A�l�b�g���[�N��NetworkManager��CentOS 6�ƕς�炸�W���Ȃ̂ŁACUI��NetworkManager�p�̃c�[���ł���nmtui���Љ�܂��B

## SysV init����systemd�ւ̈ڍs
CentOS 7����A����܂ł̃T�[�r�X�Ǘ��ł���SysV init�A�܂���Upstart����Linux�����̐V�����T�[�r�X�Ǘ��}�l�[�W���[�ł���usystemd�v�ɒu���������܂����B/etc/rc.d�f�B���N�g���ȉ��̃T�[�r�X�N���X�N���v�g���g������������߂��܂����B

�ȒP��systemd�ł̃T�[�r�X�Ǘ��ɂ��ĉ�����܂��B

### ���j�b�g�ł̊Ǘ�
�]���������x����T�[�r�X�ƌĂ΂�Ă����d�g�݂́Asystemd�ł́u���j�b�g�v�Ƃ��čĒ�`����܂����B���j�b�g�ɂ́A�u�^�[�Q�b�g�v�i�������x���ɑ����j���j�b�g��u�T�[�r�X�v���j�b�g������A���ꂼ��̃��j�b�g�͈ˑ��֌W�̒�`���ł���悤�ɂȂ��Ă��܂��B

�ˑ��֌W�Ƃ́A���Ƃ��΁u���̃T�[�r�X�����s����ɂ͂��炩���߂��̃T�[�r�X�����s����Ă��Ȃ���΂Ȃ�Ȃ��v�Ƃ����֌W�ł��B�]����SysV init�ł̓T�[�r�X�ɂ͈ˑ��֌W�������������߁A�T�[�r�X�����ԂɎ��s����Ƃ������@�ňˑ��֌W���������Ă��܂����B�������A���s�̏��Ԃ�ۏ؂��邽�߂�1�����s����u���񏈗��v�ƂȂ邽�߁A�V�X�e���N�����x���Ȃ�Ƃ�����_������܂����B

systemd�ł͈ˑ��֌W�ɂȂ��T�[�r�X���u���񏈗��v�Ŏ��s���邽�߁A�����ɃV�X�e�����N���ł���Ƃ������_������܂��B

��ȃ��j�b�g�̎�ނ͈ȉ��̒ʂ�ł��B

|���j�b�g|����|
|-------|-------|
|service|�]���̃T�[�r�X�Ɠ��l|
|target|�T�[�r�X�����܂Ƃ߂邽�߂̃��j�b�g|
|mount|�}�E���g�|�C���g|
|swap|�X���b�v�̈�|
|device|�f�o�C�X|

### �T�[�r�X�̑���
systemd�ł́A�T�[�r�X�̋N�����~���s���̂�systemctl�R�}���h���g�p���܂��B����͏]����service�R�}���h�ɑ������܂��B

Web�T�[�r�X�̋N�����~�A�ċN���A�����ď�Ԃ̊m�F���s���ɂ́A�ȉ���systemctl�R�}���h���g�p���܂��B

#### �T�[�r�X�̋N��
systemctl start�R�}���h�ŁA�T�[�r�X���N�����܂��B

```shell-session
# systemctl start httpd
```

#### �T�[�r�X�̃X�e�[�^�X�m�F
systemctl status�R�}���h�ŁA�T�[�r�X�̃X�e�[�^�X���m�F�ł��܂��B

systemd�ł́A�T�[�r�X�̃v���Z�X���u�R���g���[���O���[�v�v�icgroup�j�Ƃ���Linux�J�[�l���̎d�g�݂Ŏ��s����悤�ɕς��܂����Bcgroup���g�����ƂŁACPU�⃁�����Ȃǂ̃��\�[�X���_��Ɋ��蓖�Ă邱�Ƃ��ł��闘�_������܂��B

```shell-session
# systemctl status httpd
httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled)
   Active: active (running) since �� 2015-01-28 15:23:50 JST; 33s ago
 Main PID: 2926 (httpd)
   Status: "Total requests: 0; Current requests/sec: 0; Current traffic:   0 B/sec"
   CGroup: /system.slice/httpd.service
           ����2926 /usr/sbin/httpd -DFOREGROUND
           ����2927 /usr/sbin/httpd -DFOREGROUND
           ����2928 /usr/sbin/httpd -DFOREGROUND
           ����2929 /usr/sbin/httpd -DFOREGROUND
           ����2930 /usr/sbin/httpd -DFOREGROUND
           ����2931 /usr/sbin/httpd -DFOREGROUND

 1�� 28 15:23:50 centos7.example.com httpd[2926]: AH00557: httpd: apr_sockad...
 1�� 28 15:23:50 centos7.example.com httpd[2926]: AH00558: httpd: Could not ...
 1�� 28 15:23:50 centos7.example.com systemd[1]: Started The Apache HTTP Ser...
Hint: Some lines were ellipsized, use -l to show in full.
```

#### �T�[�r�X�̍ċN��
systemctl restart�R�}���h�ŁA�T�[�r�X���ċN�����܂��B

```shell-session
# systemctl restart httpd
# systemctl status httpd
httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled)
   Active: active (running) since �� 2015-01-28 15:24:40 JST; 2s ago
  Process: 2945 ExecStop=/bin/kill -WINCH ${MAINPID} (code=exited, status=0/SUCCESS)
 Main PID: 2950 (httpd)
�i���j
```

#### �T�[�r�X�̒�~
systemctl stop�R�}���h�ŁA�T�[�r�X���~���܂��B

```shell-session
# systemctl stop httpd
# systemctl status httpd
httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled)
   Active: inactive (dead)
```

### ���j�b�g�ꗗ�̎擾
systemd�ŊǗ�����Ă��郆�j�b�g�̈ꗗ���擾����ɂ́Asystemctl list-unit-files�R�}���h�����s���܂��B

```shell-session
# systemctl list-unit-files
```

���ׂĂ̎�ނ̃��j�b�g���\������Ă��܂��̂ŁA���j�b�g�̎�ނ��i�荞�ނɂ�-t�I�v�V������t�^���Ď��s���܂��B

���Ƃ��΁Aservice���j�b�g������\������ɂ͈ȉ���systemctl�R�}���h�����s���܂��B����͏]����chkconfig --list�R�}���h�ɑ������܂��B

```shell-session
# systemctl list-unit-files -t service
```

�\�������X�e�[�^�X�iSTATE�j�̈Ӗ��͈ȉ��̒ʂ�ł��B


|�X�e�[�^�X|�Ӗ�|
|-------|-------|
|enabled|�V�X�e���N�����Ɏ��s�����|
|disabled|�V�X�e���N�����Ɏ��s����Ȃ�|
|static|�V�X�e���N�����̎��s�̗L���͐ݒ�ł��Ȃ�|

### ���݂̃��j�b�g�̏󋵂��m�F
���݂̃��j�b�g�̏󋵂��m�F����ɂ́Asystemctl list-units�R�}���h�����s���܂��Bsystemctl�R�}���h�̃f�t�H���g�͂��̃T�u�R�}���h�̎w��ɂȂ��Ă��܂��B

�ȉ��̗�͓������ʂ�Ԃ��܂��B

```shell-session
# systemctl list-units
# systemctl
```

-t�I�v�V�������g���āAservice���j�b�g�����ɍi�荞�ނ��Ƃ��ł��܂��B

```shell-session
# systemctl -t service
UNIT                         LOAD   ACTIVE SUB     DESCRIPTION
abrt-ccpp.service            loaded active exited  Install ABRT coredump hook
abrt-oops.service            loaded active running ABRT kernel log watcher
abrt-xorg.service            loaded active running ABRT Xorg log watcher
abrtd.service                loaded active running ABRT Automated Bug Reporting 
alsa-state.service           loaded active running Manage Sound Card State (rest
atd.service                  loaded active running Job spooling tools
�i���j
kdump.service                loaded failed failed  Crash recovery kernel arming
�i���j
```

�\���̈Ӗ��͈ȉ��̒ʂ�ł��B

|����|�Ӗ�|
|-------|-------|
|UNIT|���j�b�g��|
|LOAD|systemd�ւ̐ݒ�̓ǂݍ��ݏ�|
|ACTIVE|���s��Ԃ̊T�v�Bactive��inactive�ŕ\�����|
|SUB|���s��Ԃ̏ڍׁBrunning�i���s���j��exited�i���s�������I�������j�Ȃǂŕ\�����B|
|DESCRIPTION|���j�b�g�̐���|

�f�t�H���g�ł́A����ACTIVE�̎��s��Ԃ�active�ɂȂ��Ă�����݂̂̂��\������Ă��܂��Binactive�̃��j�b�g���\������ɂ�--all�I�v�V������t�^���Ď��s���܂��B

����LOAD�́Asystemctl mask�R�}���h�Ŗ�����������masked�ɕς��܂��B�ڍׂ͌�q���܂��B

����ACTIVE��failed�ɂȂ��Ă���ƁA���炩�̌����ŋN�����s���Ă���Ƃ������ƂɂȂ�܂��B��L�̗�ł́Akdump�i�J�[�l���_���v�j�T�[�r�X�̋N���Ɏ��s���Ă��܂��B

### �f�o�C�X�ꗗ�̊m�F
-t device�I�v�V������t�^���āA�f�o�C�X�ꗗ��\�����܂��B

```shell-session
# systemctl list-units -t device
UNIT                                                                                     LOAD   ACTIVE SUB     DESCRIPTION
sys-devices-pci0000:00-0000:00:05.0-virtio0-net-eth0.device                              loaded active plugged Virtio network device
sys-devices-pci0000:00-0000:00:1f.2-ata3-host2-target2:0:0-2:0:0:0-block-sda-sda1.device loaded active plugged CentOS_7-0_SSD
�i���j
```

### �}�E���g�󋵂̊m�F
-t mount�I�v�V������t�^���āA�}�E���g�̏󋵈ꗗ��\�����܂��B

```shell-session
# systemctl list-units -t mount
UNIT                         LOAD   ACTIVE SUB     DESCRIPTION
-.mount                      loaded active mounted /
boot.mount                   loaded active mounted /boot
dev-hugepages.mount          loaded active mounted Huge Pages File System
dev-mqueue.mount             loaded active mounted POSIX Message Queue File Syst
home.mount                   loaded active mounted /home
�i���j
```

### �X���b�v�󋵂̊m�F
-t swap�I�v�V������t�^���āA�X���b�v�̏󋵈ꗗ��\�����܂��B

```shell-session
# systemctl list-units -t swap
UNIT             LOAD   ACTIVE SUB    DESCRIPTION
dev-dm\x2d0.swap loaded active active /dev/dm-0
�i���j
```

### �T�[�r�X�̎����N���̐ݒ�
�V�X�e���N�����ɃT�[�r�X�������N������ɂ́Asystemctl enable�R�}���h�����s���܂��B����͏]����chkconfig�R�}���h�ɑ������܂��B

��Ƃ��āAWeb�T�[�r�X���V�X�e���N�����Ɏ����N������悤�ɐݒ肵�܂��B/usr/lib/systemd/system/httpd.service��Web�T�[�r�X�̋N���X�N���v�g�ł��Bsystemctl enable�R�}���h�����s����ƁA/etc/systemd/system/multi-user.target.wants�f�B���N�g���ɃV���{���b�N�����N���쐬����܂��B

���̓���́Amulti-user.target�^�[�Q�b�g���j�b�g���Ăяo���ꂽ���ɁA�V���{���b�N�����N�̋N���X�N���v�g�����s�����悤�ɐݒ肵�Ă��܂��BSysV init�ɂ�����/etc/init.d�f�B���N�g�����̃T�[�r�X�N���X�N���v�g��/etc/rc.d�f�B���N�g�����Ƀ������x�����ɍ쐬�����V���{���b�N�����N�̊֌W�ɑ������܂��B

```shell-session
# systemctl enable httpd
ln -s '/usr/lib/systemd/system/httpd.service' '/etc/systemd/system/multi-user.target.wants/httpd.service'
```

�V�X�e���N�����̎����N�����s��Ȃ��悤�ɂ���ɂ́Asystemctl disable�R�}���h�����s���܂��B�쐬���ꂽ�V���{���b�N�����N���폜����A�N���X�N���v�g�͌Ăяo����Ȃ��Ȃ�܂��B

```shell-session
# systemctl disable httpd
rm '/etc/systemd/system/multi-user.target.wants/httpd.service'
```

### �T�[�r�X��systemd����̏��O
systemctl mask�R�}���h�����s����ƁA�w�肵���T�[�r�X��systemd�̊Ǘ����珜�O����A�蓮�ł̋N�����s���Ȃ��Ȃ�܂��B

����Ƃ��ẮA/etc/systemd/system/httpd.service��/dev/null�ւ̃V���{���b�N�����N�Ƃ��č쐬����A���̋N���X�N���v�g���Ăяo����Ă������s���Ȃ��Ȃ�܂��B

Web�T�[�r�X��systemd���珜�O���܂��B

```shell-session
# systemctl mask httpd
ln -s '/dev/null' '/etc/systemd/system/httpd.service'
# systemctl start httpd
Failed to issue method call: Unit httpd.service is masked.
```

systemctl is-enabled�R�}���h�ŁA�T�[�r�X�̏�Ԃ��m�F�ł��܂��Bhttpd�T�[�r�X�̏�Ԃ�masked�ƂȂ��Ă��܂��B

```shell-session
# systemctl is-enabled httpd
masked
```

systemctl unmask�R�}���h�����s����ƁA�V���{���b�N�����N���폜����āA�w�肵���T�[�r�X��systemd�ŊǗ������悤�ɂȂ�܂��Bhttpd�T�[�r�X�̏�Ԃ�disabled�ɂȂ�܂��B

```shell-session
# systemctl unmask httpd
rm '/etc/systemd/system/httpd.service'
# systemctl is-enabled httpd
disabled
```

### systemd�̃T�[�r�X�Ɋ֘A����f�B���N�g���ƃV�X�e���N���̎d�g��
systemd�������I�ɂǂ̂悤�Ȏd�g�݂ɂȂ��Ă���̂��A�֘A����f�B���N�g����������܂��B

systemctl enable�R�}���h�̓�������Ă�������ʂ�Asystemd�̎d�g�݂ɂ����āA�֘A����f�B���N�g���͈ȉ���2�ł��B

#### /usr/lib/systemd/system�f�B���N�g��
�T�[�r�X�N���X�N���v�g���i�[����Ă��܂��B/etc/rc.d/init.d�f�B���N�g���ɑ������܂��B

#### /etc/systemd/system�f�B���N�g��
�T�[�r�X�N���X�N���v�g�ɑ΂���V���{���b�N�����N���z�u����܂��B/etc/rc.d�f�B���N�g���ɑ������܂��B

�V�X�e���N������systemd�̓���́A/etc/systemd/system�f�B���N�g���ȉ��̃T�u�f�B���N�g�����ɍ쐬���ꂽ�T�[�r�X�N���X�N���v�g�ւ̃V���{���b�N�����N���������s����ăT�[�r�X���N������܂��B�V���{���b�N�����N�̍쐬�����ꏊ�́A�����ʂ̃^�[�Q�b�g���j�b�g���Ƀf�B���N�g�����������Ă��܂��B

�^�[�Q�b�g���̃f�B���N�g���Ƃ��̖����A���s�̏��Ԃ͈ȉ��̒ʂ�ł��B

#### 1. /etc/systemd/system/sysinit.target.wants/
�V�X�e���̏����Ɏ��s�����X�N���v�g�ł��Brc.sysinit�X�N���v�g�ɑ������܂��B

#### 2. /etc/systemd/system/basic.target.wants/
�V�X�e�����ʂɎ��s�����X�N���v�g�ł��B

#### 3. /etc/systemd/system/multi-user.target.wants/
�]���̃������x��3�iCUI�j�ɑ������܂��B

#### 4. /etc/systemd/system/graphical.target.wants/
�]���̃������x��5�iGUI�j�ɑ������܂��B

SysV init�ł̓������x��3�ƃ������x��5�͕ʁX�̈����ł������Asystemd�ł�multi-user.target�����s���graphical.target�����s�����悤�ɂȂ��Ă��܂��B

�ǂ��܂Ŏ��s���邩�́A���ɐ�������f�t�H���g�^�[�Q�b�g�̐ݒ�ɂ���Č��߂��Ă��܂��B

### �f�t�H���g�^�[�Q�b�g�̕ύX
systemd�ł̓������x���ł͂Ȃ��A�T�[�r�X�N���X�N���v�g�����ԂɎ��s���Ă����A�f�t�H���g�^�[�Q�b�g�Ŏw�肳�ꂽ�^�[�Q�b�g�܂Ŏ��s���܂��B�f�t�H���g�^�[�Q�b�g��ύX���邱�ƂŁACUI�N�������邩�AGUI�N���ɂ��邩��I���ł��܂��B

�f�t�H���g�^�[�Q�b�g�̕ύX�́Asystemctl set-default�R�}���h�����s���܂��B����́ASysV init�̐ݒ�t�@�C��/etc/inittab�Ŏw�肵�Ă���N�����������x���iinitdefault�j�̕ύX�ɑ������܂��B

#### �f�t�H���g�^�[�Q�b�g�̊m�F
systemctl get-default�R�}���h�ŁA���݂̃f�t�H���g�^�[�Q�b�g���m�F���܂��B

```shell-session
# systemctl get-default
graphical.target
```

#### �f�t�H���g�^�[�Q�b�g��CUI�ɕύX
�f�t�H���g�^�[�Q�b�g��multi-user.target�ɕύX���A�ċN�����܂��BCUI�ŋN�����Ă��邱�Ƃ��m�F���܂��B

```shell-session
# systemctl set-default multi-user.target
# reboot
```

#### �f�t�H���g�^�[�Q�b�g��GUI�ɕύX
GUI�ł̋N���ɖ߂��ɂ́A�ȉ���systemctl set-default�R�}���h�����s���܂��B

```shell-session
# systemctl set-default graphical.target
# reboot
```

### ���݂̃^�[�Q�b�g�̈ꎞ�I�ȕύX
systemd�ł̌��݂̃^�[�Q�b�g���ꎞ�I�ɕύX����ɂ́Asystemctl isolate�R�}���h�����s���܂��B����́ASysV init�̃������x���ύX�itelinit�R�}���h�j�ɑ������܂��B

GUI����CUI�ɕύX���܂��BGUI���O�C�����Ă���ꍇ�A���O�A�E�g���܂��B

```shell-session
# systemctl isolate multi-user.target
```

CUI����GUI�ɕύX���܂��B

```shell-session
# systemctl isolate graphical.target
```

## journald�ɂ�郍�O�L�^
systemd�ɂ̓T�[�r�X�Ȃǂ���̃��O���L�^����journald���p�ӂ���Ă���Asyslog�Ƃ͕ʂɃ��O���L�^����Ă��܂��B

### journald�̃��O�̊m�F
journald�̃��O���m�F����ɂ́Ajournalctl�R�}���h�����s���܂��B�I�v�V������t�^���Ȃ��Ŏ��s����ƁA���ׂẴ��O���\������܂��B

�ȉ��̗�ł́Admesg�R�}���h�Ŋm�F�ł���Linux�J�[�l���N�����̃��O���L�^����Ă���̂�������܂��B

```shell-session
# journalctl
-- Logs begin at �� 2015-01-28 17:29:04 JST, end at �� 2015-01-28 17:29:38 JST. 
 1�� 28 17:29:04 centos7.example.com systemd-journal[149]: Runtime journal is us
 1�� 28 17:29:04 centos7.example.com systemd-journal[149]: Runtime journal is us
�i���j
```


����̃T�[�r�X�̃��O�ɍi��ɂ́A-u�I�v�V������t�^���Ď��s���܂��B

�ȉ��̗�ł́Ahttpd�T�[�r�X�N�����̃��O���m�F�ł��܂��B

```shell-session
# journalctl -u httpd
-- Logs begin at �� 2015-01-28 17:29:04 JST, end at �� 2015-01-28 17:31:34 JST. 
 1�� 28 17:31:28 centos7.example.com systemd[1]: Starting The Apache HTTP Server
 1�� 28 17:31:34 centos7.example.com httpd[2232]: AH00557: httpd: apr_sockaddr_i
 1�� 28 17:31:34 centos7.example.com httpd[2232]: AH00558: httpd: Could not reli
 1�� 28 17:31:34 centos7.example.com systemd[1]: Started The Apache HTTP Server.
```

### journald�̃��O�̕ۑ�
journald�̃��O�́A�ċN������Ə����Ă��܂��ݒ肪�f�t�H���g�ƂȂ��Ă��܂��Bjournald�̐ݒ�t�@�C��/etc/systemd/journald.conf��Storage�ݒ�̒l���f�t�H���g�ł�auto�ɐݒ肳��Ă��܂��B���̐ݒ�́A�ȉ��̂悤�ɓ��삵�܂��B

1. /var/log/journal�f�B���N�g�������݂���Ώ�������
1. /var/log/journal�f�B���N�g�������݂��Ȃ����A�������߂Ȃ��ꍇ�ɂ́A/run/log/journal�f�B���N�g���ɏ�������

�f�t�H���g�ł�/var/log/journal�f�B���N�g���͑��݂��Ȃ����߁A/run/log/journal�f�B���N�g���Ƀ��O���������܂�܂��B/run/log/journal�f�B���N�g����tmpfs�Ń�������ɍ��ꂽ�ꎞ�̈�Ȃ̂ŁA�V�X�e���ċN�����Ƀ��O�̃t�@�C���͏����Ă��܂��܂��B

journald�̃��O���V�X�e���ċN�����ɏ����Ȃ��悤�ɂ���ɂ́A�ȉ��̂悤��/var/log/journal�f�B���N�g�����쐬���āA�V�X�e�����ċN�����܂��B

```shell-session
# mkdir /var/log/journal
# chmod 700 /var/log/journal
# reboot
```

���O�t�@�C�����쐬���ꂽ���Ƃ��m�F���܂�

```shell-session
# ls -l /var/log/journal/
���v 0
drwxr-sr-x. 2 root systemd-journal 49  1�� 28 14:53 3b71b9857a284561a3450996bf78a306
# ls -l /var/log/journal/3b71b9857a284561a3450996bf78a306/
���v 16392
-rw-r-----. 1 root root            8388608  1�� 28 14:56 system.journal
-rw-r-----+ 1 root systemd-journal 8388608  1�� 28 14:55 user-42.journal
```

## firewalld�ɂ��p�P�b�g�t�B���^�����O
CentOS 7�ł́ALinux�J�[�l���̃p�P�b�g�t�B���^�����O�̎d�g�݂ł���iptables��firewalld�T�[�r�X���Ǘ����Ă��܂��Bfirewalld�𗘗p����ƕ��G�ȃp�P�b�g�t�B���^�����O�������ł��܂����A�����ł͊�{�I�Ȑݒ��������܂��B

�܂��A���G�Ȑݒ肪�s�v�ȏꍇ�ɂ͏]����iptables�T�[�r�X�ɂ��Ǘ��ɖ߂����Ƃ��ł��܂��B

### firewalld�̐ݒ�m�F
firewalld�ł́A�p�P�b�g�t�B���^�����O�̐ݒ���u�]�[���v�Ƃ����d�g�݂ŊǗ����Ă��܂��B

�]�[�����w�肵�Ȃ������ꍇ�ɗ��p�����f�t�H���g�]�[�����m�F����ɂ́Afirewall-cmd�R�}���h��--get-default-zone�I�v�V������t�^���Ď��s���܂��B�f�t�H���g�ł�public�Ƃ����]�[�������p�����̂�������܂��B

```shell-session
# firewall-cmd --get-default-zone
public
```

�f�t�H���g�]�[��public�̐ݒ���m�F���܂��BDHCP�N���C�A���g��SSH��������Ă��܂��B

```shell-session
# firewall-cmd --list-all
public (default, active)
  interfaces: eth0
  sources:
  services: dhcpv6-client ssh
  ports:
  masquerade: no
  forward-ports:
  icmp-blocks:
  rich rules:
```

�f�t�H���g�]�[���ŋ�����Ă���T�[�r�X�������m�F����ɂ́A--list-services�I�v�V������t�^���܂��B

```shell-session
# firewall-cmd --list-services
dhcpv6-client ssh
```

��`����Ă���T�[�r�X���m�F���܂��B�����Ŋm�F�ł���T�[�r�X���]�[���ɓK�p���邱�ƂŁA��M�p�P�b�g�����ł��܂��B

```shell-session
# firewall-cmd --get-services
amanda-client bacula bacula-client dhcp dhcpv6 dhcpv6-client dns ftp high-availability http https imaps ipp ipp-client ipsec kerberos kpasswd ldap ldaps libvirt libvirt-tls mdns mountd ms-wbt mysql nfs ntp openvpn pmcd pmproxy pmwebapi pmwebapis pop3s postgresql proxy-dhcp radius rpc-bind samba samba-client smtp ssh telnet tftp tftp-client transmission-client vnc-server wbem-https
```

### firewalld��HTTP��������
firewalld�̐ݒ��ύX���āAHTTP�̎�M�������܂��B

--add-service�I�v�V�����Œ�`����Ă���T�[�r�X���]�[���ɓK�p���܂��B

--permanent�I�v�V������t�^����ƁA�]�[���̐ݒ�t�@�C���ł���/etc/firewalld/zones/public.xml���C������āA�V�X�e���ċN����ł�HTTP�̎�M���������悤�ɂȂ�܂��B

```shell-session
# firewall-cmd --add-service=http  --permanent
success
# firewall-cmd --list-services
dhcpv6-client http ssh
# cat /etc/firewalld/zones/public.xml
<?xml version="1.0" encoding="utf-8"?>
<zone>
  <short>Public</short>
  <description>For use in public areas. You do not trust the other computers on networks to not harm your computer. Only selected incoming connections are accepted.</description>
  <service name="dhcpv6-client"/>
  <service name="http"/>
  <service name="ssh"/>
</zone>
```

Web�T�[�r�X���N�����A�O������Web�T�[�o�ɐڑ��ł��邱�Ƃ��m�F���܂��B

```shell-session
# systemctl start httpd
```

### iptables��L���ɂ���
firewalld�T�[�r�X���~���Aiptables�T�[�r�X��L���ɂ���ɂ͈ȉ��̃R�}���h�����s���܂��B

```shell-session
# systemctl stop firewalld
# systemctl disable firewalld
# systemctl enable iptables
# systemctl start iptables
```

firewalld�T�[�r�X��L���ɖ߂��ɂ́A�ȉ��̃R�}���h�����s���܂��B

```shell-session
# systemctl stop iptables
# systemctl disable iptables
# systemctl enable firewalld
# systemctl start firewalld
```

*NetworkManager�p�Ǘ��c�[�� nmtui
CentOS 7�ł���������NetworkManager���g���ăl�b�g���[�N���Ǘ����܂��B

NetworkManager�ł́A�ݒ�t�@�C���𒼐ڕҏW���邱�Ƃ͐�������Ă��܂���BGUI��CUI�p�̊Ǘ��c�[�����񋟂���Ă���̂ŁA�c�[�����g���Đݒ��ύX���܂��B

![GUI��NetworkManager�ݒ���](nmtui1.png)

GUI�ł́u�V�X�e���c�[���v���j���[����u�ݒ�v�����s���邱�ƂŃl�b�g���[�N�̐ݒ���s���܂��B

![CUI��NetworkManager�ݒ���](nmtui2.png)

CUI�ł�nmtui�����s���邱�ƂŁA�ȒP�Ƀl�b�g���[�N���ݒ�ł��܂��B�l�b�g���[�N�C���^�[�t�F�[�X��IP�A�h���X���̐ݒ��A�L���^�����̐؂�ւ����s����悤�ɂȂ��Ă��܂��B

