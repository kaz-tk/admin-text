# �g���u���V���[�e�B���O

## ���O�Ǘ�
�V�X�e����Q�̖��������͂���g���u���V���[�e�B���O���s���ꍇ�ɁA�����Ƃ��L�v�ȏ�񌹂����O�ł��B

���O�ɂ́AOS���o�͂��郍�O�A�A�v���P�[�V�������o�͂��郍�O�ȂǑ����̎�ނ����݂��܂��B

�����ł́A��\�I�ȃ��O�̎�ނƊm�F���@�A�ݒ���@�Ȃǂ�������܂��B

### ���O�̎��
CentOS�ł́A���O�t�@�C����/var/log�f�B���N�g���ȉ��Ɋi�[����Ă��܂��B

�ȉ��͑�\�I�ȃ��O�t�@�C���ł��B

|�t�@�C����|���e|
|-------|-------|
|messages|�T�[�r�X�N�����̏o�͂Ȃǈ�ʓI�ȃ��O|
|secure|�F�؁A�Z�L�����e�B�֌W�̃��O|
|maillog|���[���ԘA�̃��O|
|dmesg|�J�[�l�����o�͂������b�Z�[�W�̃��O|

### ���O�̊m�F
�T�[�o�̃��O�ɃT�[�r�X�N�����A�܂��͓��쎞�̃G���[���O���L�^����Ă��Ȃ������m�F���܂��B�܂��A�N���C�A���g���ɂ��G���[���O���L�^����Ă��Ȃ������m�F���܂��B

* ��ʓI�ȃg���u���ł���΁A�܂���/var/log/messages���m�F���܂��B
* �F�؊֌W��A�N�Z�X�����Ɋ֌W����g���u����/var/log/secure���m�F���܂��B
* ���[���֌W�ł����/var/log/maillog���m�F���܂��B
* Web�T�[�o�ł����/var/log/httpd/error_log�Ȃǂ��m�F���܂��B

### dmesg�ɋL�^����郍�O
dmesg�R�}���h�́udisplay message�v�̗��ŁALinux�J�[�l�������b�Z�[�W���o�͂��郊���O�o�b�t�@�i�z�o�b�t�@�j�̓��e��\�����܂��B���̃����O�o�b�t�@�͈��̃T�C�Y���ŏz����悤�ɂȂ��Ă���A�Â����O�͏����Ă����܂��B
dmesg�R�}���h��p���邱�Ƃɂ��A�V�X�e���N�����ɏo�͂����J�[�l�����b�Z�[�W�̊m�F���ł��܂��B�J�[�l�����������n�[�h�E�F�A��F�����Ă��邩�ǂ������m�F����ꍇ�ȂǂɎQ�Ƃ��܂��B

```shell-session
# dmesg
Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
Linux version 2.6.32-504.el6.x86_64 (mockbuild@c6b9.bsys.dev.centos.org) (gcc version 4.4.7 20120313 (Red Hat 4.4.7-11) (GCC) ) #1 SMP Wed Oct 15 04:27:16 UTC 2014
Command line: ro root=/dev/mapper/vg_server-lv_root rd_LVM_LV=vg_server/lv_swap rd_NO_LUKS rd_LVM_LV=vg_server/lv_root rd_NO_MD crashkernel=auto  KEYBOARDTYPE=pc KEYTABLE=jp106 LANG=ja_JP.UTF-8 rd_NO_DM rhgb quiet
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
  Centaur CentaurHauls
Disabled fast string operations
�i���j
```

### syslog�ɂ���
syslog�́A�J�[�l����v���O�����Ȃǂ���o�͂���郍�O���܂Ƃ߂ċL�^����d�g�݂ł��Bsyslog���g�����ƂŁA�e�v���O�����͓Ǝ��Ƀ��O���L�^����d�g�݂��J������K�v�������Ȃ�܂��B�܂��Asyslog�T�[�o���l�b�g���[�N��œ��삳���邱�ƂŁA�����̃z�X�g����̃��O���܂Ƃ߂ċL�^���邱�ƂŁA���O���ꌳ�Ǘ����邱�Ƃ��ł��܂��B
CentOS 6�ł́Asyslog�T�[�o�Ƃ���rsyslog���g�p�ł��܂��B

rsyslog�́A�]����syslog�f�[�����isyslogd�j�ɒu�������A�}���`�X���b�h��syslog�f�[�����ł��Brsyslog�iReliable syslog�j�Ƃ������O�����������ʂ�A�����M��������������悤�ɊJ������Ă��܂��B���̂��߁A���O�̓]����TCP���g�p������A�f�[�^�x�[�X�ւ̃��O�ۑ��A�Í����������O�̓]���Ȃǂ��s�����Ƃ��ł��܂��B��{�I�Ȑݒ�ɂ��ẮA�]����syslogd�ƌ݊���������܂��B

### �t�@�V���e�B�ƃv���C�I���e�B
�J�[�l����v���O�������o�͂���syslog���b�Z�[�W�ɂ́A�u�t�@�V���e�B�v�ifacility�j�Ɓu�v���C�I���e�B�v�ipriority�j�ƌĂ΂��l���ݒ肳��Ă��܂��B

�t�@�V���e�B�́A�������̃��O���b�Z�[�W�𐶐������̂����w�肵�܂��B���Ƃ��΁A�J�[�l���⃁�[���Ƃ������l���w�肳��܂��B

�܂��A�v���C�I���e�B�̓��b�Z�[�W�̏d�v�����w�肵�܂��B���Ƃ��΁A�P�Ȃ���A���Ɋ댯�ȏ�ԂȂǂƂ������l���w�肳��܂��B

�t�@�V���e�B�ɂ́A�ȉ��̎�ނ�����܂��B

|�t�@�V���e�B|�Ӗ�|
|-------|-------|
|auth|�Z�L�����e�B�E�F�؊֘A�ilogin�Asu �Ȃǁj|
|authpriv|�Z�L�����e�B�E�F�؊֘A�i�v���C�x�[�g�j|
|cron|cron��at�̃��O|
|daemon|��ʓI�ȃf�[�����i�T�[�o�v���O�����j�֘A|
|kern|�J�[�l���֘A|
|lpr|�v�����^�֘A|
|mail|���[���֘A|
|news|NetNews�֘A|
|security|auth�Ɠ���|
|syslog|syslogd���g�̃��O|
|user|���[�U�A�v���P�[�V�����̃��O|
|uucp|uucp�]�����s���v���O�����̃��O|
|local0����local7|�Ǝ��̃v���O�����ŗ��p�\��facility|

�v���C�I���e�B�ɂ́A�ȉ��̎�ނ�����܂��B

|�v���C�I���e�B|�Ӗ�|
|-------|-------|
|debug|�f�o�b�O�p���b�Z�[�W|
|info|��ʓI�ȏ�񃁃b�Z�[�W|
|notice|�ʒm���b�Z�[�W|
|warning|�x�����b�Z�[�W|
|warn|warning�Ɠ���|
|err|��ʓI�ȃG���[���b�Z�[�W|
|error|err�Ɠ���|
|crit|�n�[�h��Q�Ȃǂ̊댯�ȃG���[���b�Z�[�W|
|alert|�V�X�e���j���Ȃǂً̋}����|
|emerg|���Ɋ댯�ȏ��|
|panic|emerg�Ɠ���|
|none|�t�@�V���e�B�𖳌��ɂ���|

### syslog�T�[�o�̐ݒ�
syslog�T�[�o�̐ݒ�t�@�C���ł���/etc/rsyslog.conf�ɂ́A�󂯎�������O���b�Z�[�W���t�@�V���e�B�ƃv���C�I���e�B�̑g�ݍ��킹�łǂ̃t�@�C���ɏo�͂��邩�̐ݒ肪�L�q����Ă��܂��B

�L�q�͈ȉ��̌`���ƂȂ�܂��B

```
�t�@�V���e�B.�v���C�I���e�B	�A�N�V����
```

syslog�T�[�o�̐ݒ�t�@�C�����ŁA�����̃t�@�V���e�B���w�肵�����ꍇ�ɂ́A�u,�v�i�R���}�j�ŋ�؂�܂��B���Ƃ��΁AUUCP�]���ƃ��[���֘A�̃t�@�V���e�B�𓯎��Ɏw�肵�����ꍇ�ɂ́A�ȉ��̂悤�Ɏw�肵�܂��B

```shell-session
uucp,news.crit	/var/log/spooler
```

syslog�ݒ�t�@�C�����Ńv���C�I���e�B���w�肷��ƁA���̃v���C�I���e�B�ȏ�̏d�v�x�̃v���C�I���e�B�����ׂē��Ă͂܂�܂��B���Ƃ��΁A�ȉ��̂悤�ɐݒ肵���Ƃ��܂��B

```
mail.warning
```

mail�t�@�V���e�B�����warning�ȏ�ierr�Acrit�Aalert�Aemerg�j�̂��ׂẴv���C�I���e�B�����Ă͂܂�܂��B

����̃v���C�I���e�B�̂ݎw�肵�����ꍇ�ɂ́A�u=�v���C�I���e�B�v�Ǝw�肵�܂��B

```
mail.=warning
```

���̎w���mail�t�@�V���e�B�̃v���C�I���e�B��warning�̃��b�Z�[�W�݂̂����Ă͂܂�܂��B

none�t�@�V���e�B�͂�����ȓ���������̂ŁA��q�̗�ŉ�����܂��B

### �A�N�V�����̐ݒ�
�t�@�V���e�B�ƃv���C�I���e�B���L�q�����E���ɁA�Y�����郍�O���ǂ����邩���w�肷��A�N�V�������L�q���܂��B

��ȃA�N�V�����́A�ȉ��̕\�̂Ƃ���ł��B

#### �t�@�C����
���O���t�@�C���ɏ������ށB

#### -�t�@�C����
���O���t�@�C���ɏ������ލۂɃo�b�t�@�����O����B�������ݐ��\�����シ�邪�A�������܂�Ă��Ȃ��f�[�^�����鎞�ɃV�X�e����Q����������ƃ��O��������B

#### \�v���O����
���O���b�Z�[�W���v���O�����Ɉ����n���B

#### *
���ׂẴ��[�U�̃R���\�[���Ƀ��b�Z�[�W��\������B

#### @�z�X�g���i���邢��IP�A�h���X�j
UDP��syslog�T�[�o�Ƀ��O���b�Z�[�W�𑗐M����B

#### @@�z�X�g���i���邢��IP�A�h���X�j
TCP��syslog�T�[�o�Ƀ��O���b�Z�[�W�𑗐M����B

### syslog�T�[�o�̃f�t�H���g�ݒ���m�F����
�ݒ�t�@�C��/etc/rsyslog.conf�Ɋ��ɐݒ肳��Ă�����e���m�F���܂��B

```shell-session
authpriv.*	/var/log/secure
```

���̐ݒ�́A�t�@�V���e�B��authpriv�i�F�؊֌W�j�A�v���C�I���e�B��*�i�S�Ẵv���C�I���e�B�j�̃��O���b�Z�[�W��/var/log/secure�ɏo�͂���悤�Ɏw�肵�Ă��܂��B

```shell-session
*.info;mail.none;authpriv.none;cron.none		/var/log/messages
```

���̐ݒ�́A���ׂẴt�@�V���e�B��info�v���C�I���e�B�ȏ�̃��O�����ׂ�/var/log/messages�ɏo�͂���悤�ɂ��Ă��܂��B�������Amail�Aauthpriv�Acron��3�̃t�@�V���e�B�ɂ�none�v���C�I���e�B���w�肳��Ă��邽�߁A�Ώۂ���͏��O����Ă��܂��B

���O���ꂽ�e�t�@�V���e�B�̏o�͂́A�ȉ��̂悤�ɕʓr�w�肳��Ă��܂��B

mail�t�@�V���e�B�̃��O�́A��������ɂ�����x�o�b�t�@�����O������Ń��O�t�@�C���ɏ������ނ悤�Ɂu-�i�n�C�t���j�v���w�肵�Ă��܂��B���[���T�[�o�͈�x�ɑ�ʂ̃��O���������ނ��Ƃ���������ł��B

```shell-session
authpriv.*						/var/log/secure
mail.*							-/var/log/maillog
cron.*							/var/log/cron
```

### �J�[�l�����O��syslog�o�͐ݒ�
�f�t�H���g�̐ݒ�ł̓R�����g�A�E�g����Ė����ɂȂ��Ă���J�[�l������̃��O�o�͂̐ݒ��L���ɂ��܂��B�J�[�l���̃��O�́A���Ƃ���iptables�̂悤�ȃJ�[�l���̋@�\�����O���o�͂��܂��B

iptables�̐ݒ�t�@�C��/etc/sysconfig/iptables��ҏW���A�|�[�g�ԍ�22�Ԃ̋��iACCEPT�j�ƁA���̑��̑S�Ă����ہiREJECT�j���郋�[���̊ԂɁA���O���擾���郋�[����ǉ����܂��B

```shell-session
# Firewall configuration written by system-config-firewall
# Manual customization of this file is not recommended.
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT
��-A INPUT -j LOG --log-level debug --log-prefix '[iptables_test]:' ���V�K�ɒǉ�
-A INPUT -j REJECT --reject-with icmp-host-prohibited
-A FORWARD -j REJECT --reject-with icmp-host-prohibited
COMMIT
```

iptables�T�[�r�X��reload���āA�V�����ݒ��ǂݍ��܂��܂��B

```shell-session
# service iptables reload
iptables: Trying to reload firewall rules:                 [  OK  ]
```

/etc/rsyslog.conf��ҏW���A�t�@�V���e�B��kern�A�v���C�I���e�B���S�Ẵ��b�Z�[�W��/var/log/kern.log�ɏo�͂���ݒ��ǉ����܂��B

```shell-session
# vi /etc/rsyslog.conf

# Log all kernel messages to the console.
# Logging much else clutters up the screen.
#kern.*                                                 /dev/console
��kern.*                                                 /var/log/kern.log ���V�K�ɒǉ�
```

rsyslog�T�[�r�X���ċN�����āA�V�����ݒ��ǂݍ��܂��܂��B

```shell-session
# service rsyslog restart
�V�X�e�����K�[���~��:                                    [  OK  ]
�V�X�e�����K�[���N����:                                    [  OK  ]
```

�O���̃z�X�g����ݒ���s�����z�X�g�ɑ΂��āAiptables�ŋ�����Ă��Ȃ��|�[�g�ԍ�80�Ԃ�Web�u���E�U���ŃA�N�Z�X���܂��B

/var/log/kern.log�Ƀ|�[�g�ԍ�80�Ԃɑ΂���ʐM�����ۂ����|�̃��O���o�͂���܂��B

```shell-session
# tail /var/log/kern.log 
Dec 25 14:54:16 server kernel: imklog 5.8.10, log source = /proc/kmsg started.
Dec 25 14:54:50 server kernel: ��'[iptables_test]:'��IN=eth0 OUT= MAC=00:1c:42:65:af:c4:00:1c:42:00:00:08:08:00 SRC=192.168.0.2 DST=192.168.0.10 LEN=64 TOS=0x00 PREC=0x00 TTL=64 ID=24955 DF PROTO=TCP SPT=57191 ��DPT=80�� WINDOW=65535 RES=0x00 SYN URGP=0 
```

### �����[�g�z�X�g�̃��O��UDP�Ŏ󂯎��
syslog�T�[�o�Ƃ��ă����[�g�z�X�g�̃��O���󂯎�邽�߂̐ݒ���s���܂��Bsyslog�̃��b�Z�[�W�̑���M�́A�ʏ�UDP�ōs���܂��B

�ݒ�t�@�C��/etc/rsyslog.conf���ɂ���ȉ���2�s����A�s���̃R�����g�A�E�g���폜���Đݒ��L���ɂ��܂��B

$ModLoad�́AUDP�p�̃v���g�R�����W���[���̃��[�h��ݒ肵�Ă��܂��B$UDPServerRun�́AUDP�Ń��O���b�Z�[�W���󂯎��|�[�g�ԍ����w�肵�Ă��܂��B

```shell-session
[root@server ~]## vi /etc/rsyslog.conf

�i���j
# Provides UDP syslog reception
$ModLoad imudp �����s����#���폜
$UDPServerRun 514 �����s����#���폜
```

rsyslog�T�[�r�X���ċN�����܂��Brsyslogd��UDP�̃|�[�g�ԍ�514�Ԃő҂��󂯂�悤�ɂȂ�܂��B

```shell-session
[root@server ~]# service rsyslog restart
�V�X�e�����K�[���~��:                                    [  OK  ]
�V�X�e�����K�[���N����:                                    [  OK  ]
[root@server ~]# lsof -i:514
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
rsyslogd 9282 root    3u  IPv4 134339      0t0  UDP *:syslog 
rsyslogd 9282 root    4u  IPv6 134340      0t0  UDP *:syslog 
```

�ݒ��Aiptables�̐ݒ��ύX���AUDP�̃|�[�g�ԍ�514�Ԃւ̃p�P�b�g��������悤�ɐݒ��ύX����K�v������܂��B�ݒ�ɂ��Ă͌�q���܂��B

### �����[�g�z�X�g�̃��O��TCP�Ŏ󂯎��
���O���b�Z�[�W�̑���M��TCP���g�p���邱�Ƃɂ��AUDP�Ŕ������Ă������O�̎�肱�ڂ���h�����Ƃ��ł��܂��BUDP�̓Z�b�V�������X�ȃv���g�R���̂��߁A����M�Ɏ��s�������ɍđ��M����d�g�݂��������߂ł��B

�������ATCP�̓v���g�R���̐�����UDP�����������d���Ȃ��Ă��܂����߁A��ʂ̃��O�����M����Ă�����ł͋t�Ƀ{�g���l�b�N�ɂȂ��Ă��܂��Asyslog�T�[�o���������ׂŏ������؂��Ă��܂��\��������܂��B

���̂��߁ATCP���g�������O���b�Z�[�W�̑���M�́A���O�̗ʂ�����قǑ����Ȃ����O�L�^�̐M�������K�v�ȏꍇ�ɐݒ肵�܂��B�����A��ʂ̃��O�����M����Ă���ꍇ�ɂ́Asyslog�T�[�o�𕡐��p�ӂ��邩�AUDP���g���K�v������܂��B

�ݒ�t�@�C��/etc/rsyslog.conf���ɂ���ȉ���2�s����A�s���̃R�����g�A�E�g���폜���Đݒ��L���ɂ��܂��B

$ModLoad�́ATCP�p�̃v���g�R�����W���[���̃��[�h��ݒ肵�Ă��܂��B$InputTCPServerRun�́ATCP�Ń��O���b�Z�[�W���󂯎��|�[�g�ԍ����w�肵�Ă��܂��B

```shell-session
[root@server ~]# vi /etc/rsyslog.conf

�i���j
# Provides TCP syslog reception
$ModLoad imtcp �����s����#���폜
$InputTCPServerRun 514 �����s����#���폜
```

rsyslog�T�[�r�X���ċN�����܂��Brsyslogd��TCP�̃|�[�g�ԍ�514�Ԃő҂��󂯂�悤�ɂȂ�܂��B

```shell-session
[root@server ~]# service rsyslog restart
�V�X�e�����K�[���~��:                                    [  OK  ]
�V�X�e�����K�[���N����:                                    [  OK  ]
[root@server ~]# lsof -i:514
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
rsyslogd 24138 root    1u  IPv4 107209      0t0  TCP *:shell (LISTEN)
rsyslogd 24138 root    3u  IPv4 107202      0t0  UDP *:syslog 
rsyslogd 24138 root    4u  IPv6 107203      0t0  UDP *:syslog 
rsyslogd 24138 root    8u  IPv6 107210      0t0  TCP *:shell (LISTEN)
```

�|�[�g��shell�ƕ\������Ă���̂́A�|�[�g�ԍ��̐ݒ�t�@�C��/etc/services�Œ�`����Ă��邽�߂ł��B����ɉe���͂���܂���B

```shell-session
# grep 514 /etc/services
shell           514/tcp         cmd             # no passwords used
syslog          514/udp
�i���j
```

�ݒ��Aiptables�̐ݒ��ύX���ATCP�̃|�[�g�ԍ�514�Ԃւ̃p�P�b�g��������悤�ɐݒ��ύX����K�v������܂��B

### syslog�T�[�o��iptables�̐ݒ�
syslog�T�[�o��iptables�̐ݒ��ύX���ATCP�����UDP�̃|�[�g�ԍ�514�Ԃ̐ڑ��������Ă����܂��B���邢�́Aiptables�T�[�r�X���~���Ă����܂��B

```shell-session
[root@server ~]# service iptables stop
iptables: �`�F�C�����|���V�[ ACCEPT �֐ݒ蒆filter         [  OK  ]
iptables: �t�@�C�A�E�H�[�����[����������:                  [  OK  ]
iptables: ���W���[�������O����:                          [  OK  ]
```

/etc/sysconfig/iptables�ւ�iptables�̃��[����ǉ�����ɂ́A�ȉ��̂悤�ɂȂ�܂��B�p�P�b�g��Reject���郋�[���̑O�ɁA���[���ݒ��ǉ����܂��B���[���ݒ��ǉ�������iptables�T�[�r�X��reload���Ă����܂��B

```shell-session
[root@server ~]# vi /etc/sysconfig/iptables
�i���j
��-A INPUT -m state --state NEW -m udp -p udp --dport 514 -j ACCEPT ���V�K�ɒǉ�
��-A INPUT -m state --state NEW -m tcp -p tcp --dport 514 -j ACCEPT ���V�K�ɒǉ�
-A INPUT -j REJECT --reject-with icmp-host-prohibited
```

### syslog�N���C�A���g�̐ݒ�
�l�b�g���[�N�Őڑ����ꂽsyslog�T�[�o�ɑ΂��ă��O���b�Z�[�W�𑗐M����syslog�N���C�A���g��ݒ肵�܂��B

syslog�N���C�A���g���̃z�X�g�ł�rsyslog��ݒ肵�A�A�N�V�����̐ݒ�Ńl�b�g���[�N���syslog�T�[�o���w�肵�܂��B

syslog�N���C�A���g�̐ݒ�t�@�C��/etc/rsyslog.conf���C�����܂��B

authpriv�t�@�V���e�B�Ɋւ��邷�ׂẴ��O��syslog�T�[�o�ɑ��M����悤�ɐݒ��ǉ����܂��B@���M��Ǝw�肷�邱�Ƃ�UDP���g�p�������M���w��ł��܂��B

�܂��Amail�t�@�V���e�B�Ɋւ��邷�ׂẴ��O��syslog�T�[�o�ɑ��M����悤�ɐݒ��ǉ����܂��B@@���M��Ǝw�肷�邱�Ƃ�TCP���g�p�������M���w��ł��܂��B

```shell-session
# vi /etc/rsyslog.conf

# The authpriv file has restricted access.
authpriv.*                                              /var/log/secure
��authpriv.*                                              @192.168.0.10 ���V�K�ɒǉ�

# Log all the mail messages in one place.
mail.*                                                  -/var/log/maillog
��mail.*                                                  @@192.168.0.10 ���V�K�ɒǉ�```

syslog�N���C�A���g��rsyslog�T�[�r�X���ċN�����܂��B

```shell-session
[root@client ~]# service rsyslog restart
�V�X�e�����K�[���~��:                                    [  OK  ]
�V�X�e�����K�[���N����:                                    [  OK  ]
```

#### UDP�Ń��O�𑗐M
syslog�N���C�A���g��logger�R�}���h�����s���āAauthpriv.debug�v���C�I���e�B�Ń��O���o�͂��܂��B

```shell-session
[root@client ~]# logger -p authpriv.debug "This is auth log over UDP"
```

syslog�T�[�o���/var/log/secure�Ƀ��O���o�͂���邱�Ƃ��m�F���܂��B

```shell-session
[root@server ~]# tail -f /var/log/secure 
�i���j
Dec 25 17:16:50 client root: This is auth log over UDP
```

#### TCP�Ń��O�𑗐M
syslog�N���C�A���g��logger�R�}���h�����s���āAmail.debug�v���C�I���e�B�Ń��O���o�͂��܂��B

```shell-session
[root@client ~]# logger -p mail.debug "This is mail log over TCP"
```

syslog�T�[�o���/var/log/maillog�Ƀ��O���o�͂���邱�Ƃ��m�F���܂��B

```shell-session
[root@server ~]# tail /var/log/secure
�i���j
Dec 25 17:18:03 client root: This is mail log over TCP
```

### logrotate�ɂ�郍�O���[�e�[�V����
���O�t�@�C���͏�ɒǋL����Ă������߁A�t�@�C���T�C�Y������ɔ�剻���ăf�B�X�N�e�ʂ��������A��Ń��O���m�F����ۂɕK�v�ȃ��O�������ɂ����Ȃ�܂��B�����̖���������邽�߁A���O�������ԂŃ��[�e�[�V��������logrotate���g���Ă��܂��B

logrotate�́Acron����1��1��A/etc/cron.daily/logrotate�X�N���v�g�ɂ���ċN������܂��B/etc/logrotate.conf��logrotate�̐ݒ�t�@�C���ƂȂ��Ă���A���O�t�@�C�������[�e�[�V��������^�C�~���O��A���O�t�@�C����������܂Ŏc�����Ȃǂ̐ݒ肪�L�q����Ă��܂��B�T�[�r�X���̏ڍׂȐݒ�́A/etc/logrotate.d�f�B���N�g���Ɋi�[����Ă��܂��B

logrotate�̐ݒ�Ŏg�p�ł���f�B���N�e�B�u�͈ȉ��̂Ƃ���ł��B

#### create [���[�h] [���L���[�U] [���L�O���[�v]
���[�e�[�V�������s������A����ɋ�̐V�K���O�t�@�C�����쐬���܂��B�������w��ł��܂��B���[�h��0755�̂悤�Ȑ��l�����B�w�肵�Ȃ������ɂ��Ă͌��̃t�@�C���̑����������p����܂��B

#### nocreate
create���O���[�o���ɐݒ肵���ꍇ�ɁA�ʂ�create�𖳌��ɂ������ۂɎg�p���܂��B

#### copy/nocopy
���̃��O�t�@�C���͂��̂܂܂ɂ��āA�R�s�[��ۑ����܂��B

#### copytruncate/nocopytruncate
copy�̓�����s������A���̃��O�t�@�C���̓��e���������܂��B�������I�ɂ�create�Ɠ������ʂƂȂ�܂��B����̓��O�t�@�C���������[�h������@�������v���O�����ւ̑Ώ��@�̂ЂƂł��B���Ƃ���Oracle 10g R1/R2��alert���O�ɑ΂��ẮA���̕��@���s��Ȃ��ƈȑO�̃��O�t�@�C���i�Ⴆ��alert_xx.log.1�j�Ƀ��O���������ݑ������܂��B

#### rotate ���㐔
���ネ�[�e�[�V�����̐��㐔���w�肵�܂��B���Ƃ��Ό��̃��O�t�@�C����a.log�̏ꍇ�Anum��2���w�肷��ƁAa.log��a.log.1��a.log.2���p���ƂȂ�܂��B0�̏ꍇ�Aa.log���p���ƂȂ�܂��B

#### start ���l
�ŏ��̃��[�e�[�V�����t�@�C���̖����ɕt������l���w�肵�܂��B�f�t�H���g��1�ł��B���Ƃ���num��5���w�肷��ƁAa.log��a.log.5��a.log.6�ƂȂ�܂��B

#### extension �g���q
���[�e�[�V�������������O�t�@�C���ɕt����g���q���w�肵�܂��B�w��ɂ͋�؂�̃h�b�g���K�v�ł��B���Ƃ��Ίg���q�Ɂu.bak�v�Ǝw�肷��ƁAsome.log�̏��ネ�[�e�[�V�������O��some.log.1.bak�ƂȂ�܂��B���k���s���ꍇ�A���k�ɂ��g���q�͂���ɂ��̌��ɕt���܂��B

#### compress/nocompress
���[�e�[�V����������̋��t�@�C���Ɉ��k���|���܂��B�f�t�H���g��nocompress�i�񈳏k�j�ł��B

#### compresscmd �R�}���h
���O�t�@�C���̈��k�Ɏg�p����v���O�������w�肵�܂��B�f�t�H���g��gzip�ł��B

#### uncompresscmd �R�}���h
���O�t�@�C���̉𓀂Ɏg�p����v���O�������w�肵�܂��B�f�t�H���g��gunzip�ł��B

#### compressoptions �I�v�V����
���k�v���O�����֓n���I�v�V�������w�肵�܂��B�f�t�H���g��gzip�ɓn���u-9�v�i���k���ő�j�ł��B�u-9 -s�v�̂悤�ɃX�y�[�X����ŕ����̃I�v�V�������w�肷�邱�Ƃ͂ł��܂���B

#### compressext �g���q
���k��̃t�@�C���ɕt����g���q�i�h�b�g���K�v�j���w�肵�܂��B�f�t�H���g�ł́A�g�p���鈳�k�R�}���h�ɉ��������̂��t�����܂��B

#### delaycompress/nodelaycompress
���k���������̃��[�e�[�V�����܂Œx�点��A���邢�͒x�点�܂���B

#### olddir �f�B���N�g��/noolddir
���[�e�[�V�������������O���f�B���N�g���Ɉړ����܂��B�ړ���͌��Ɠ����f�o�C�X��Ŏw�肵�܂��B���̃��O�ɑ΂��鑊�Ύw����L���ł��B

#### mail address/nomail
�����O�t�@�C����address�ɑ��M���܂��B�ǂ̒i�K�̃��O�𑗂邩��maillast�Ȃǂ̃I�v�V�����Ō��܂�܂��B

#### maillast
���オ�I����Ĕj������郍�O�����[�����܂��B

#### mailfirst
���ネ�[�e�[�V�������O�����[�����܂��B

#### daily/weekly/monthly
���O���[�e�[�V���������/�T��/�����ɍs���܂��B�f�t�H���g��daily�B���Ƃ���weekly�Ȃ�A�������s�����Ƃ��Ă��A�T��1�񂾂����[�e�[�V�������s���܂��B

#### size �T�C�Y[K/M]
���O�̃T�C�Y���T�C�Y�o�C�g�𒴂��Ă���΃��[�e�[�V�������s���܂��B���̏�����daily,weekly�Ȃǂ̏������D�悳��܂��B�L���o�C�g�iK�j�A���K�o�C�g�iM�j�ł̎w����ł��܂��B

#### ifempty/notifempty
���̃��O�t�@�C������ł����[�e�[�V�������s���A���邢�͍s���܂���B

#### missingok/nomissingok
�w��̃��O�t�@�C�������݂��Ȃ������Ƃ��Ă��G���[���o�����ɏ����𑱍s����A���邢�̓G���[���o�͂��܂��B

#### firstaction
���[�e�[�V�������s���O�ɃX�N���v�g�����s���܂��Bprerotete�����O�Ɏ��s�����ʒ�`���ł̂ݎw��\�ł��B

#### prerotate
���[�e�[�V�������s���O�ɃX�N���v�g�����s���܂��Bfirstaction�̌�Ɏ��s����܂��B�ʒ�`���ł̂ݎw��ł��܂��B

#### postrotate
���[�e�[�V�������s��ꂽ��ɃX�N���v�g�����s���܂��Blastaction���O�Ɏ��s����܂��B�ʒ�`���ł̂ݎw��ł��܂��B

#### lastaction
���[�e�[�V�������s��ꂽ��i������j�ɃX�N���v�g�����s���܂��Bpostrotate�̌�Ɏ��s����܂��B�ʒ�`���ł̂ݎw��ł��܂��B

#### sharedscripts
���[�e�[�V�������郍�O�������������ꍇ�ɁAprerotate�Apostrotate�̃X�N���v�g����x�������s���܂��B

#### nosharedscripts
���[�e�[�V�������郍�O�������������ꍇ�ɁAprerotate�Apostrotate�̃X�N���v�g���e���O�t�@�C�����Ɏ��s���܂��B

#### include �t�@�C���i�f�B���N�g���j
include�̋L�q�̂���ʒu�ɕʂ̐ݒ�t�@�C����ǂݍ��݂܂��B�f�B���N�g�����w�肵���ꍇ�A���̃f�B���N�g��������A�f�B���N�g������і��O�t���p�C�v�ȊO�̒ʏ�t�@�C�����A���t�@�x�b�g���ɓǂݍ��܂�܂��B

#### tabooext [+] �g���q[,�g���q,...]
include�Ńf�B���N�g�����w�肵���ꍇ�ɓǂݍ��ރt�@�C�����珜�O����t�@�C���̊g���q���w�肵�܂��B�f�t�H���g�Łu.rpmorig�v�u.rpmsave�v�u,v�v�u.swp�v�u.rpmnew�v�u~�v�u.cfsaved�v�u.rhn-cfg-tmp-*�v���w�肳��Ă��܂��B+���w�肷��ƃf�t�H���g�w��ɑ΂��Ēǉ��Ŋg���q���w��ł��܂��B+���w�肵�Ȃ��ƃf�t�H���g�w���j�����ĐV�K�Ɋg���q���w�肵�܂��B

### ���O���[�e�[�g�ݒ�t�@�C���̊m�F
/etc/logrotate.d/httpd���Q�l�ɁA���[�e�[�g�̐ݒ���m�F���܂��B

```shell-session
# cat /etc/logrotate.d/httpd 
/var/log/httpd/*log {
    missingok
    notifempty
    sharedscripts
    delaycompress
    postrotate
        /sbin/service httpd reload > /dev/null 2>/dev/null || true
    endscript
}
```

���̗�ł́A�ȉ��̒ʂ胍�O���[�e�[�V�����̏������s���܂��B

�ΏۂƂȂ郍�O�t�@�C����/var/log/httpd�f�B���N�g�����́A�t�@�C������log�ŏI��邷�ׂẴ��O�t�@�C���ł��B�f�t�H���g�ł�access_log�Aerror_log�Ƃ����t�@�C�����̃��O�t�@�C�����쐬����Ă��܂��B

* 1�s�ڂ�missingok�Ń��O�t�@�C�������݂��Ȃ������Ƃ��Ă��G���[���o�����ɏ����𑱍s���܂��B
* 2�s�ڂ�notifempty�Ō��̃��O�t�@�C������Ȃ�΃��[�e�[�V�������܂���B
* 3�s�ڂ�sharedscripts��prerotate,postrotate �̃X�N���v�g����x�������s���܂��B
* 4�s�ڂ�delaycompress�ň��k���������̃��[�e�[�V�����܂Œx�点�܂��B
* 5�s�ڂ�"postrotate"����"endscript"�܂ł��A���[�e�[�V�������s��ꂽ��Ɏ��s�����X�N���v�g�ł��Bservice�R�}���h�����s����httpd�T�[�r�X��reload���邱�ƂŁA�V�������O�t�@�C������������܂��B

## �l�b�g���[�N�c�[�����g�����g���u���V���[�e�B���O
�T�[�o�ɐڑ��ł��Ȃ��Ȃǃl�b�g���[�N�ɋN�������肪���������ꍇ�A��{�I�Ȍ����̒������s�����߂̃c�[���Ƃ��āA�ȉ��̂悤�ȃl�b�g���[�N�c�[�����g�p���܂��B

* ping
* traceroute
* netstat
* tcpdump
* Wireshark

�����̃c�[�����g�p�����A�g���u���V���[�e�B���O�ɂ��ĉ�����܂��B��ʓI�ɂ́A�O������T�[�r�X�ւ̐ڑ����ł��Ȃ��Ȃ����ꍇ�ɂ́A�ȉ��̂悤�Ȏ菇�Ō����̒������s���܂��B

1. ���O�̊m�F
1. ping�R�}���h�ɂ��IP�ʐM�̊m�F
1. telnet�R�}���h�ɂ��TCP�ʐM�̊m�F
1. netstat�R�}���h�ɂ��|�[�g�̏󋵂̊m�F
1. �ʐM���e�̊m�F

### ping�R�}���h�ɂ��IP�ʐM�̊m�F
ping�R�}���h���g���āA�T�[�o�ɑ΂���ʐM���s���邩�ǂ������m�F���܂��Bping�R�}���h��ICMP���g�����ʐM��IP�ʐM���\���m�F�ł��܂��B�T�[�o�ɑ΂���ping�ɉ����������ꍇ�A�ȉ��̂悤�Ȗ�肪�l�����܂��B

#### �T�[�o���g�̖��
IP�A�h���X��f�t�H���g�Q�[�g�E�F�C���K�؂ɐݒ肳��Ă��Ȃ�������Aiptables�Ȃǂ̃p�P�b�g�t�B���^�����O��ICMP��ʂ��Ȃ��ݒ�ɂȂ��Ă��邱�Ƃ��l�����܂��B
�T�[�o�̃l�b�g���[�N�ݒ���ēx�m�F���Ă݂܂��B�܂��A�T�[�o�����瑼�̃z�X�g��ping�R�}���h�����s���āA���������邩�m�F���Ă݂܂��B

#### �l�b�g���[�N�o�H�̖��
�l�b�g���[�N�ʐM�o�H��ɂ���P�[�u����X�C�b�`�A���[�^�[�A�t�@�C�A�[�E�H�[���⃍�[�h�o�����T�[�Ȃǂ̃l�b�g���[�N�@��ɖ�肪���������m�F���܂��B
���[�e�B���O�ɖ�肪���邩���m�F���邽�߂ɂ�traceroute�R�}���h���g�p���܂����Atraceroute�R�}���h��ICMP���g�p���Ă��邽�߁A�r���̃��[�^�[��ICMP��ʂ��Ȃ��ꍇ�A���ׂĂ̌o�H���m�F�ł��Ȃ����Ƃ�����܂��B

### telnet�R�}���h�ɂ��TCP�ʐM�̊m�F
telnet�R�}���h��2�Ԗڂ̈����Ƀ|�[�g�ԍ����w�肵�āA�T�[�o�̃T�[�r�X�ɐڑ����邱�Ƃ��ł���̂ŁATCP�ʐM���\���m�F�ł��܂��B

```
telnet �ڑ���IP�A�h���X �|�[�g�ԍ�
```

�������A�f�B�X�g���r���[�V�����ɂ���Ă�telnet�R�}���h���C���X�g�[������Ă��Ȃ��̂ŁA�C���X�g�[������K�v������܂��B

```shell-session
# yum install telnet
```

�T�[�r�X�ɐڑ��ł��Ȃ��ꍇ�ɂ́A�ȉ��̂悤�Ȗ�肪�l�����܂��B

#### �l�b�g���[�N�o�H�̖��
iptables��l�b�g���[�N�o�H��̃t�@�C�A�[�E�H�[���ȂǂŁA�w�肳�ꂽ�|�[�g�ւ̒ʐM��������Ă��Ȃ��B
iptables��t�@�C�A�[�E�H�[���̃|�[�g���ݒ���m�F���܂��B

#### �T�[�o���g�̖��
�T�[�r�X����~���Ă���A�w�肳�ꂽ�|�[�g��Listen���Ă��Ȃ��B���邢�́A���[�J�����[�v�o�b�N�A�h���X�i127.0.0.1�j�̂�Listen���Ă���A�ڑ���Ɏw�肵��IP�A�h���X�Ƀ|�[�g���o�C���h����Ă��Ȃ��B
netstat�R�}���h��lsof�R�}���h�Ȃǂ��g�p���āA�|�[�g�̏�Ԃ��m�F���܂��B

### netstat�ł̃|�[�g�̏󋵂̊m�F
netstat�R�}���h���g���āA�T�[�r�X�v���Z�X�ƃ|�[�g�ԍ��A�����IP�A�h���X�Ƃ̃o�C���h�̏󋵂��m�F�ł��܂��B

netstat�R�}���h��-p�I�v�V�������w�肵�Ď��s���܂��B

```shell-session
# netstat -anp | grep sshd
tcp        0      0 0.0.0.0:22     0.0.0.0:*  LISTEN   1493/sshd
```

���̌��ʂ���A�ȉ��̂��Ƃ�������܂��B

* sshd�̃v���Z�XID��1493�ł��邱��
* TCP�|�[�g�ԍ�22�Ԃ�LISTEN���Ă��邱��
* �|�[�g�ԍ�22�Ԃ��T�[�o�̂��ׂĂ�IP�A�h���X�i0.0.0.0:22�j�Ƀo�C���h����Ă��邱��
* ���M���������s���Ă��Ȃ����Ɓi0.0.0.0:*�j

### �p�P�b�g�L���v�`���ɂ��ʐM���e�̊m�F
�T�[�o�Ƃ̐ڑ����s���Ă���A���O�ɂ��肪����ƂȂ�G���[���������A�T�[�r�X�����������삵�Ȃ��悤�ȏꍇ�ɂ́A�ʐM�p�P�b�g���L���v�`�����āA�ʐM���e���m�F���܂��B�p�P�b�g���L���v�`�����邱�ƂŁA�T�[�o�ƃN���C�A���g�̊Ԃłǂ̂悤�ȒʐM���s���Ă��邩���m�F�ł��܂��B
�p�P�b�g�L���v�`���̃c�[���Ƃ��ẮA�V���v���ɋ@�\����tcpdump�R�}���h�ƁAGUI�ő���ł���Wireshark�Ȃǂ�����܂��B

### tcpdump�R�}���h���g�����p�P�b�g�L���v�`��
tcpdump�R�}���h�́A����M���Ă���p�P�b�g���L���v�`�����āA���̏���W���o�͂ɏo�͂���R�}���h�ł��B
tcpdump�R�}���h�̓f�t�H���g�ł͑S�Ẵp�P�b�g�̏����o�͂���̂ŁA�I�v�V�����ŏo�͌��ʂ��t�B���^�����O���āA�K�v�ȏ��𓾂���悤�ɂ��܂��B

��Ƃ��āA-i�I�v�V�����Ńl�b�g���[�N�C���^�[�t�F�[�X���w�肵�āAeth0��ʂ��ē����Ă���ʐM�̃p�P�b�g���擾���Ă݂܂��B

�T�[�o���tcpdump�R�}���h�����s���܂��B���ʂ����_�C���N�g���āAtcpdump.out�t�@�C���ɋL�^���܂��B

```shell-session
# tcpdump -i eth0 > tcpdump.out
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
```

�N���C�A���g����SSH�ŃT�[�o�Ƀ��O�C�����A���O�A�E�g���܂��B

�T�[�o��Ctrl+C�L�[����͂��āAtcpdump�R�}���h���I�����܂��B

```shell-session
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
��^C��216 packets captured ����Ctrl+C�L�[�����
216 packets received by filter
0 packets dropped by kernel
```

�쐬���ꂽtcpdump.out�t�@�C���̓��e���m�F���܂��B

```shell-session
# grep ssh tcpdump.out
13:17:06.041096 IP client.example.com.43880 > server.example.com.ssh: ��Flags [S]��, seq 4050960604, win 14600, options [mss 1460,sackOK,TS val 13231 ecr 0,nop,wscale 6], length 0
13:17:06.041125 IP server.example.com.ssh > client.example.com.43880: ��Flags [S.]��, seq 3335753529, ��ack 4050960605��, win 14480, options [mss 1460,sackOK,TS val 22019990 ecr 13231,nop,wscale 6], length 0
13:17:06.041240 IP client.example.com.43880 > server.example.com.ssh: ��Flags [.]��, ��ack 1��, win 229, options [nop,nop,TS val 13231 ecr 22019990], length 0
```

�����玞�ԁi�}�C�N���b�P��)�A���M��IP�A�h���X.�|�[�g�ԍ��A�ʐM�̌����̖��A����z�X�g.�|�[�g�ԍ��A�t���O�iSYN)�A�V�[�P���X�A�E�B���h�E�A�I�v�V�����A�ő�Z�O�����g�T�C�Y�ƂȂ��Ă��܂��B

#### 1�s��
�N���C�A���g�̃|�[�g43880����T�[�o�̃|�[�g22�issh�j�Ɍ�����SYN�t���O��TCP�p�P�b�g�Ƒ��M���Đڑ��̗v��

#### 2�s��
1�s�ڂ̃p�P�b�g�ɑ΂��āASYN+ACK�t���O��TCP�p�P�b�g�𑗐M

#### 3�s��
ACK�t���O��TCP�p�P�b�g�𑗐M���āATCP�̃X���[�E�F�C�n���h�V�F�C�N������

���̂悤�ɁA�T�[�o�ƃN���C�A���g�̊Ԃ̒ʐM���m�F�ł��܂��B

### Wireshark���g�����m�F
tcpdump�̏o�̓t�@�C���͏��ʂ̃p�P�b�g������ꍇ�ɂ͏[���ł����A��ʂ̃p�P�b�g���m�F����ɂ͉ǐ����Ⴂ�̂���_�ł��B

GUI�����p�P�b�g�L���v�`�������O�\�t�g�ł���Wireshark���g���΁A�p�P�b�g�L���v�`�������O���s�����p�P�b�g�̒��g��������A�t�B���^�����O�@�\�ŕK�v�ȃp�P�b�g�݂̂ɍi�荞��Ńp�P�b�g���m�F���邱�Ƃ��ł��܂��B

Wireshark���C���X�g�[�����܂��BGUI�ł��C���X�g�[�����邽�߁Awireshark-gnome�p�b�P�[�W���C���X�g�[�����܂��B

```shell-session
# yum install wireshark-gnome
```

1. Wireshark���N�����܂��B
CentOS��GUI�Ń��O�C�����A�[������wireshark�R�}���h�����s���邩�A�u�A�v���P�[�V�����v���j���[���u�C���^�[�l�b�g�v���uWireshark Network Analyzer�v���N�����܂��B

```shell-session
# wireshark &
```

��2

2. �L���v�`�����s���f�o�C�X��I�т܂��B

![�uCapture�v���j���[���uInterfaces�v��I�����܂�](wireshark1.png)

�uCapture�v���j���[���uInterfaces�v��I�����A�p�P�b�g�L���v�`�����s�������f�o�C�X��I�т܂��B

��3

3. �p�P�b�g�L���v�`�����J�n���܂��B

![eth0��I�����܂�](wireshark2.png)

�O���Ƃ̒ʐM���p�P�b�g�L���v�`�����邽�߂�eth0��I�т܂��B�uStart�v�{�^�����N���b�N���āA�p�P�b�g�L���v�`�����J�n���܂��B

��4

4. Web�T�[�o�ɃA�N�Z�X���܂��B
�T�[�o�ƒʐM���s���ăp�P�b�g�L���v�`�����s���܂��B�N���C�A���g��Web�u���E�U���N�����A�T�[�o��Web�T�[�o�ɃA�N�Z�X���܂��B

��5

5. �p�P�b�g�L���v�`�����~���܂��B
�uCapture�v���j���[���uStop�v��I�����A�p�P�b�g�L���v�`�����~���܂��B

��6

6. ���ʂ̍i�荞�݂��s���܂��B

![http�ōi�荞�݂��s���܂�](wireshark3.png)

�uFilter:�v�̃e�L�X�g�{�b�N�X�Ɂuhttp�v�Ɠ��͂��āAEnter�L�[�������či�荞�݂܂��B
�Q�Ƃ������p�P�b�g��I�����A�E�C���h�E�^�񒆂̏ڍ׏��ŁuHypertext Transfer Protocol�v���_�u���N���b�N���āAHTTP�ʐM�̓��e���m�F���܂��B

## �t�@�C���V�X�e����Q�̏C��
�t�@�C���V�X�e����Q����������OS������ɋN�����Ȃ��Ȃ����ꍇ�A�N���f�B�X�N�ł�����x�܂ŃV�X�e���N�����\�Ȃ�΃V���O�����[�U�[���[�h�ŋN��������A�N���f�B�X�N�ŃV�X�e�����N���ł��Ȃ��ꍇ�ɂ̓C���X�g�[���p�̃��f�B�A�����X�L���[���[�h�ŋN�����邱�ƂŁA�t�@�C���V�X�e�����C���ł��܂��B

### �V���O�����[�U���[�h�ł̋N��
�V���O�����[�U���[�h��Linux���N������ƁA�������x��1�ŋN�����邽�ߊe��T�[�r�X�̋N�����s��ꂸ�Aroot���[�U�������V�X�e���ɃA�N�Z�X�ł����ԂŋN�����܂��B
���Ƃ��΁A�T�[�r�X�̐ݒ���ԈႦ�����߃������x��3�⃉�����x��5�ŋN������ƃV�X�e���ɕs�����������ꍇ�ɂ́A�V���O�����[�U�[���[�h�ŋN�����Đݒ���C�����܂��B

�N�����ɕ\���ł���GRUB���j���[�ŋN���p�����[�^�[��ҏW���ăV���O�����[�h�ŋN�����܂��B

1. �N�����̃f�t�H���g�ł́A�ݒ肳�ꂽ�b���i�f�t�H���g�ł�5�b�j���߂���Ǝ����I�ɋN�����܂����A�����L�[����͂����GRUB���j���[���\������܂��B
2. �L�[�{�[�h��e�L�[�������ċN���p�����[�^�[�̕ҏW���[�h�ɓ���Akernel�s��I�����Ă����e�L�[�������A�����Ɂusingle�v�i���邢��1�j�ƃp�����[�^�[��ǋL���܂��B
3. Enter�L�[�������ĕҏW���[�h��ʂɖ߂�܂��B
4. b�L�[�������ăV���O�����[�U���[�h�N�����܂��B

![�J�[�l���p�����[�^�ŃV���O�����[�U�[���[�h�N����ݒ肵�܂�](singleuserboot.png)

��5

5. �V���O�����[�U���[�h�ŋN������ƁA�p�X���[�h������root���[�U�Ƃ��ă��O�C�����Ă����ԂƂȂ�܂��B�K�v�ɉ�����fsck�R�}���h�Ńt�@�C���V�X�e�����C��������A�ݒ�t�@�C�����C������Ȃǂ��ăg���u���̉������s���܂��B
6. �V�F������exit����ƁA�f�t�H���g�̃������x���Ɉڍs���܂��B

### �C���X�g�[��DVD���f�B�A���烌�X�L���[���[�h�ŋN��
�N���f�B�X�N�̃t�@�C���V�X�e���ɏ�Q���������āA�����OS���N���ł��Ȃ��Ȃ��Ă��܂����ꍇ�ɂ́A�C���X�g�[��DVD���f�B�A���烌�X�L���[���[�h�ŋN�����A�t�@�C���V�X�e���̏C�����s���܂��B

1. CentOS�̃C���X�g�[��DVD���f�B�A�ŃV�X�e�����N�����܂��BBIOS�ŋN���f�o�C�X�̏��Ԃ�ύX����Ȃǂ��āADVD�h���C�u����N������悤�ɂ��܂��B

1. �N�����j���[����uRescue installed system�v��I�����܂��B

![�N�����j���[](rescue1.png)

��3

1. Language�A�L�[�{�[�h���C�A�E�g�A�C����ƒ��Ƀl�b�g���[�N���g�p���邩��I�����܂��B

![Language��I�����܂�](rescue2.png)
![�L�[�{�[�h���C�A�E�g��I�����܂�](rescue3.png)
![�l�b�g���[�N�g�p�̗L����I�����܂�](rescue4.png)

��4

1. �n�[�h�f�B�X�N���������A/mnt/sysimage�ȉ��Ƀ}�E���g����|�̐������\������܂��B�uRead-Only�v��I�ԂƁA�n�[�h�f�B�X�N���ǂݎ���p�Ń}�E���g����܂��B�C�����s�����߁A�uContinue�v��I�����܂��B

![Continue��I�����܂�](rescue5.png)

��5

1. �n�[�h�f�B�X�N���������A/mnt/sysimage�ȉ��Ƀ}�E���g�ł����|���\������܂��B

![/mnt/sysimage�Ƀn�[�h�f�B�X�N���}�E���g����܂���](rescue6.png)

��6

1. ���s�����Ƃ�I�����܂��B�ushell�v��I�ԂƃV�F�����N�����܂��B�ufakd�v��I�Ԃ�First Aid Kit�����s����ăV�X�e���̌������s���܂��B�ureboot�v��I�ԂƃV�X�e�����ċN�����܂��B�ushell�v��I�����܂��B

![shell��I�����܂�](rescue7.png)

��7

1. bash���N�����܂��B/mnt/sysimage�ȉ��ɁA�n�[�h�f�B�X�N�̃��[�g�p�[�e�B�V�������}�E���g����Ă��邱�Ƃ��m�F���܂��B

![�V�F�����N�����܂�](rescue8.png)

��8

1. fsck�R�}���h�Ȃǂ𗘗p���āA�t�@�C���V�X�e���̏C����Ƃ��s���܂��B�C����Ƃ��I��������Aexit�ŃV�F�����I�����܂��B��Ƃ̑I����ʂɖ߂�܂��B

1. �ureboot�v��I�����āA�V�X�e�����ċN�����܂��B�C���X�g�[��DVD���f�B�A��DVD�h���C�u������o���Ă����܂��B

![reboot��I�����čċN�����܂�](rescue9.png)
