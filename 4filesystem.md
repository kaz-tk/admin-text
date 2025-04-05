#�t�@�C���V�X�e���̊Ǘ�

## �A�N�Z�X���̊Ǘ�
Linux��POSIX�Ŏ�����Ă���A�N�Z�X����ɏ������Ă��܂��BPOSIX�Ƃ́uPortable Operating System Interface for UNIX�v�̗��ŁAIEEE�ɂ���Ē�߂�ꂽ�AUNIX�x�[�X��OS�̎d�l�Z�b�g�ł��B���[�UID�iuid�j/�O���[�vID�igid�j�ƃp�[�~�b�V�����̑g�ݍ��킹�Ńt�@�C���ɑ΂���A�N�Z�X�����Ǘ����Ă��܂��B

### UID��GID
���[�UID�iuid�FUser Identifier)��Linux�V�X�e���Ń��[�U�����ʂ��邽�߂̃��j�[�N�Ȕԍ��ł��BLinux�Œǉ����ꂽ���[�U�J�E���g�ɂ́A���ꂼ��ʂ�uid������U���܂��B
uid��0����65535�܂ł̒l���Ƃ�܂��B0�͓��ʂȃ��[�UID�ŁA�Ǘ��Ҍ���������root���[�U�ɕt�^����Ă��܂��B

�O���[�vID�igid: Group Identifier�j�̓O���[�v�����ʂ��邽�߂̃��j�[�N�Ȕԍ��ł��BLinux�̃��[�U�́A1�ȏ�̃O���[�v�ɏ������邱�Ƃ��ł��܂��B
gid��0����65535�܂ł̒l���Ƃ�܂��B

### ���ؗp���[�U�A�O���[�v�̊m�F
�A�N�Z�X����̓���m�F�̂��߁A���ؗp�̃��[�U��p�ӂ��܂��B���ł�1�͂ō쐬���Ă��܂����A�쐬����Ă��Ȃ��ꍇ�ɂ�useradd�R�}���h�Agrooupadd�R�}���h�Ȃǂ��g�p���č쐬���ĉ������B

���[�Usato�ƃ��[�Usuzuki���쐬����Ă���A���[�Usuzuki��wheel�O���[�v��eigyou�O���[�v�ɏ������Ă��܂��B

```shell-session
# id sato
uid=500(sato) gid=500(sato) �����O���[�v=500(sato)
# id suzuki
uid=501(suzuki) gid=501(suzuki) �����O���[�v=501(suzuki),10(wheel),5000(eigyou)
```

### �ʁX�̃��[�U�Ƃ��č�Ƃ���
���[�Usato�ƃ��[�Usuzuki �ł̑�����X���[�Y�ɍs�����߁A���ꂼ��ʁX�̃��[�U�Ń��O�C�����܂��B

Linux�T�[�o�Ƃ͕ʂ̒[���ő�����s���Ă���ꍇ�ɂ́A���ꂼ��̃��[�U�Ń��O�C�����܂��B

Linux�T�[�o���X Window System�ő�����s���Ă���ꍇ�ɂ́Aroot���[�U�Ń��O�C��������A�ʁX�̃^�[�~�i�����N�����Asu�R�}���h���g���ă��[�U��؂�ւ���Ƃ悢�ł��傤�B


�^�[�~�i��A�Ń��[�Usato�ɐ؂�ւ��܂��B

```shell-session
[root@server ~]# su - sato
[sato@server ~]$ id
uid=500(sato) gid=500(sato) �����O���[�v=500(sato) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

�^�[�~�i��B�Ń��[�Usuzuki�ɐ؂�ւ��܂��B

```shell-session
[root@server ~]# su - suzuki
[suzuki@server ~]$ id
uid=501(suzuki) gid=501(suzuki) �����O���[�v=501(suzuki),10(wheel),5000(eigyou) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

### �v���Z�X�̎��s���̊Ǘ�
Linux�ł́Aroot���[�U�������đ��̃��[�U���N�������v���Z�X���~�����邱�Ƃ͂ł��܂���B

�ȉ��̗�ł́A���[�Usato��vi�G�f�B�^�ivim�j���N������/tmp�Ƀt�@�C�����쐬���悤�Ƃ��Ă���v���Z�X�����[�Usuzuki��kill�R�}���h�Œ�~���悤�Ƃ��܂����A��~�ł��܂���B


���[�Usato��vi�G�f�B�^��/tmp/sato���쐬���܂��B

```shell-session
[sato@server ~]$ vi /tmp/sato
```

���[�Usuzuki��vim�v���Z�X���m�F���܂��B

```shell-session
[suzuki@server ~]$ ps aux | grep vim
sato      6456  0.1  0.3 148100  3692 pts/2    S+   19:46   0:00 vim /tmp/sato
suzuki    6462  0.0  0.0 107464   916 pts/3    S+   19:46   0:00 grep vim
```

���[�Usuzuki�����[�Usato�����s����vim�G�f�B�^�̃v���Z�X��kill�R�}���h�Œ�~���悤�Ƃ��܂����A��~�ł��܂���B�w�肷��v���Z�XID�́Aps�R�}���h��2�Ԗڂ̕\�����ڂł��B

```shell-session
[suzuki@server ~]$ kill 6456
-bash: kill: (6456) - ������Ă��Ȃ�����ł�
```

���[�Usato�́u:q!�v�Ɠ��͂���vim�G�f�B�^���I�����܂��B

### �t�@�C���̃A�N�Z�X���̊Ǘ�
���[�Usato���쐬�����t�@�C��/tmp/sato���g���āA�A�N�Z�X���̓�������؂��܂��B

���[�Usato�Ńt�@�C��/tmp/sato�̃A�N�Z�X�����m�F���܂��B���̑��̃��[�U�ւ̃A�N�Z�X���͓ǂݎ��̂ݗ^�����Ă��܂��B

```shell-session
[sato@server ~]$ ls -l /tmp/sato
-rw-rw-r--. 1 sato sato 5 12��  9 17:51 2014 /tmp/sato
```

���[�Usuzuki��cat�R�}���h�����s���A�t�@�C��/tmp/sato�̓��e���m�F���܂��B���̑��̃��[�U�ւ̓ǂݎ��͋�����Ă���̂ŁA���e���m�F�ł��܂��B

```shell-session
[suzuki@server ~]$ cat /tmp/sato
sato
```

���[�Usuzuki�Ńt�@�C��/tmp/sato�ɒǋL���Ă݂܂��B�������݂̃A�N�Z�X���͗^�����Ă��Ȃ��̂ŃG���[�ƂȂ�܂��B

```shell-session
[suzuki@server ~]$ echo "suzuki" >> /tmp/sato
-bash: /tmp/sato: ��������܂���
```

### umask�ƃf�t�H���g�̃p�[�~�b�V�����̊֌W
umask�Ƃ́A�t�@�C����f�B���N�g�����V�K�ɍ쐬�����ۂɃf�t�H���g�̃p�[�~�b�V���������肷�邽�߂̒l�ł��Bumask�R�}���h�Ŋm�F�ł��܂��B

```shell-session
[sato@server ~]$ umask
0002
```

umask�̐ݒ�l�ɂ́A�V�����t�@�C�����쐬����ۂɐݒ肵�Ȃ��i�����Ȃ��j�p�[�~�b�V������8�i���Ŏw�肵�܂��B

||�ǂݎ��|��������|���s|
|-------|-------|-------|-------|
|�p�[�~�b�V����|r|w|x|
|8�i���l|4|2|1|

�t�@�C���ƃf�B���N�g���ł͐ݒ肳���f�t�H���g�̃p�[�~�b�V�������ς��̂ŁA���ꂼ��m�F���Ă݂܂��傤�B

### �t�@�C���쐬�̃p�[�~�b�V������umask
�t�@�C�����V�K�쐬�����ۂɂ̓t�@�C���̎��s�p�[�~�b�V����(eXecute)�͐ݒ肵�Ȃ��̂ŁA0666(rw-rw-rw-)�ɑ΂���umask�̒l���K�p����܂��B

umask��0002�Ɛݒ肳��Ă���ƁA���̑��̃��[�U�̏������݂̃p�[�~�b�V�����iw�j���ݒ肳��Ă��Ȃ��t�@�C���i-rw-rw-r--�A0664�j���쐬����܂��B

```shell-session
[sato@server ~]$ umask
0002
[sato@server ~]$ touch testfile
[sato@server ~]$ ls -l testfile
-rw-rw-r--. 1 sato sato 0  1�� 14 19:51 2015 testfile
```

### �f�B���N�g���쐬�̃p�[�~�b�V������umask
�f�B���N�g�����V�K�쐬�����ۂɂ́A���s�p�[�~�b�V����(eXecute)���K�v�ɂȂ�̂ŁA0777(rwxrwxrwx)�ɑ΂���umask�̒l���K�p����܂��B���s�p�[�~�b�V�������K�v�ɂȂ�̂́A1�͂ł����������Ƃ���A���̃f�B���N�g�����J�����g�f�B���N�g���ɂ��邽�߂ɂ͎��s�p�[�~�b�V�������K�v�ɂȂ邩��ł��B

umask��0002�Ɛݒ肳��Ă���ƁA���̑��̃��[�U�̏������݂̃p�[�~�b�V�����iw�j���ݒ肳��Ȃ��f�B���N�g���i-rwxrwxr-x�A0775�j���쐬����Ă��܂��B

```shell-session
[sato@server ~]$ umask
0002
[sato@server ~]$ mkdir testdir
[sato@server ~]$ ls -ld testdir
drwxrwxr-x. 2 sato sato 4096  1�� 14 19:52 2015 testdir
```

### umask��4���̗��R
�p�[�~�b�V�����͒ʏ�A���[�U�A�O���[�v�A���̑��̃��[�U��3�ɑ΂���A�N�Z�X�����ݒ肳��܂����Aumask�̒l��4���ɂȂ��Ă��܂��B����́A�ʏ�̃p�[�~�b�V�����̐擪�ɁAsetUID/setGID/�X�e�B�b�L�[�r�b�g��\�������܂܂�邽�߂ł��BsetUID�Ȃǂɂ��Ă͌�q���܂��B
�܂��A�ʏ�setUID�Ȃǂ��f�t�H���g�p�[�~�b�V�����Ƃ��Đݒ肷�邱�Ƃ͂Ȃ��̂ŁAumask�͐擪���ȗ�����3���Őݒ肷�邱�Ƃ��ł��܂��B
�ȉ��̗�ł́Aumask��022��3���Őݒ肵�Ă��܂����Aumask�R�}���h�̌��ʂ�0022�ɂȂ��Ă��܂��B

```shell-session
[sato@server ~]$ umask 022
[sato@server ~]$ umask
0022
```

### umask��ύX����
umask��ύX�������ꍇ�ɂ́Aumask�R�}���h�Őݒ肵��umask�l�������Ƃ��ė^���܂��B
�ȉ��̗�ł́Aumask�̒l��0022�ɕύX�����̂ŁA�V�K�ɍ쐬�����t�@�C���̃A�N�Z�X����644(-rw-r--r--)�ɐݒ肳��Ă��܂��B

```shell-session
[sato@server ~]$ umask 0022
[sato@server ~]$ touch umasktest
[sato@server ~]$ ls -l umasktest 
-rw-r--r--. 1 sato sato 0  1�� 14 19:53 2015 umasktest
```

### root���[�U��umask�ƃf�t�H���g��umask
��ʃ��[�U��umask�̒l��0002�ł����Aroot���[�U��umask�̒l��0022�ɐݒ肳��Ă��܂��B

```shell-session
[root@server ~]# umask
0022
```

����́Abash�V�F�����N������ۂɓǂݍ��܂��V�F���X�N���v�g/etc/bashrc�̒��Ńf�t�H���g��umask���ݒ肳��Ă��邽�߂ł��B�ȉ��̂悤�ɁAuid��200�ȏ�ŁA����uid��gid�������ꍇ�ɂ�umask�̒l��0002�i002��3���\�L�j�A����ȊO��0022�ɐݒ肳���悤�ɏ�������Ă��܂��B

���l�̏�����/etc/profile�ł��s���Ă��܂��B

```shell-session
# cat /etc/bashrc
�i���j
    # By default, we want umask to get set. This sets it for non-login shell.
    # Current threshold for system reserved uid/gids is 200
    # You could check uidgid reservation validity in
    # /usr/share/doc/setup-*/uidgid file
    if [ $UID -gt 199 ] && [ "`id -gn`" = "`id -un`" ]; then
       umask 002
    else
       umask 022
    fi
�i���j
```

uid��gid�������ł��邱�Ƃ��m�F���Ă���̂́Auseradd�R�}���h�Ń��[�U�A�J�E���g��V�K�ɍ쐬����ƁA���ʐݒ肵�Ȃ�����w�肳�ꂽ���[�U���Ɠ������O�̃O���[�v���쐬���Auid��gid�������ɂȂ邽�߂ł��B�܂�Auid��gid���������[�U�́Auseradd�R�}���h���g���ăV���v���ɍ쐬���ꂽ���[�U�A�J�E���g�Ɣ���ł���Ƃ������ƂɂȂ�܂��B

### setUID�̊m�F
setUID�����s�t�@�C���ɐݒ肳��Ă���ƁA���̎��s�t�@�C���͏��L���[�U�̌����Ŏ��s����܂��BsetUID���ݒ肳��Ă���ꍇ�Als�R�}���h�̏o�͂ŏ��L���[�U�̎��s�p�[�~�b�V�������us�v�ƕ\������܂��B

setUID���ݒ肳��Ă����Ƃ��āApasswd�R�}���h������܂��B��ʃ��[�U���p�X���[�h��ύX����ɂ́Aroot���[�U�������������߂�/etc/shadow�t�@�C���ɑ΂���ύX���K�v�ł��B�p�X���[�h��ύX����passwd�R�}���h�́A���L���[�U��root���[�U��setUID���ݒ肳��Ă���̂ŁA��ʃ��[�U��passwd�R�}���h�����s����ƁAroot���[�U�̌����Ŏ��s�����/etc/shadow�t�@�C���ɕύX�������邱�Ƃ��ł��܂��B

�R�}���h�����s�������[�U���u���s���[�U�v�AsetUID�Ō������ύX���ꂽ���[�U���u�������[�U�v�ƌĂт܂��B

�ȉ��̗�ł́Apasswd�R�}���h���ꎞ��~���āAps�R�}���h�Ŏ������[�U���m�F���Ă��܂��B

setUID���ݒ肳��Ă��邱�Ƃ��m�F���܂��B

```shell-session
[sato@server ~]$ ls -l /usr/bin/passwd 
-rwsr-xr-x. 1 root root 30768  2�� 22 20:48 2012 /usr/bin/passwd
```

passwd�����s���ACtrl+Z�L�[�ňꎞ��~���܂��B�ꎞ��~��A�V�F���v�����v�g�ɖ߂����߂ɂ�Enter�L�[�������K�v������܂��B

```shell-session
[sato@server ~]$ passwd
���[�U�[ sato �̃p�X���[�h��ύX�B
sato �p�Ƀp�X���[�h��ύX��
���݂�UNIX�p�X���[�h: ��Ctrl+Z�L�[����͌�AEnter�L�[������
[1]+  ��~                  passwd
```

ps�R�}���h�Ŏ������[�U���m�F���܂��Bpasswd�R�}���h�̎������[�U��root�ł��邱�Ƃ��m�F�ł��܂��B

```shell-session
[sato@server ~]$ ps aux | grep passwd
root     15052  0.0  0.2 164012  2068 pts/1    T    10:47   0:00 passwd
sato     15178  0.0  0.0 107464   916 pts/1    S+   10:48   0:00 grep passwd
```

fg�R�}���h�ňꎞ��~����passwd�R�}���h���t�H�A�O���E���h�v���Z�X�ɖ߂��ACtrl+C�L�[�ŏI�����܂��B

```shell-session
[sato@server ~]$ fg
passwd
��^C ��Ctrl+C�L�[�����
[sato@server ~]$ 
```

### setGID�̊m�F
setGID���ݒ肳��Ă���ƁA���L�O���[�v�̌����Ŏ��s����܂��BsetGID�͏��L�O���[�v�̎��s�p�[�~�b�V�������us�v�ƕ\������܂��B

setGID���ݒ肳��Ă����Ƃ��āAwrite�R�}���h��slocate�R�}���h������܂��B

```shell-session
$ ls -l /usr/bin/write
-rwxr-sr-x  1 root tty 10124 2�� 18��  2011 /usr/bin/write
$ ls -l /usr/bin/slocate
-rwxr-sr-x  1 root slocate 38516 11�� 17��  2007 /usr/bin/slocate
```

write�R�}���h�́A���O�C�����Ă��鑼�̃��[�U�ɑ΂��ă��b�Z�[�W�𑗂�R�}���h�ł��B�ȉ��̗�ł́Awrite�R�}���h���ꎞ��~���āAps�R�}���h�Ŏ����O���[�v���m�F���Ă��܂��B

2�̃��[�U�A�J�E���g�Ń��O�C�����܂��B�������[�U�A�J�E���g�ł��\���܂���B
write�R�}���h�����s���ACtrl+Z�L�[�ňꎞ��~���܂��B

```shell-session
[sato@server ~]$ write suzuki
��^Z ��Ctrl+Z�L�[�����
[1]+  ��~                  write suzuki
```

ps�R�}���h�Ŏ����O���[�v���m�F���܂��B

```shell-session
[sato@server ~]$ ps a -eo "%p %u %g %G %y %c" | grep write
23400 sato     sato     ��tty��      pts/1    write
```

�\���͍�����A�v���Z�XID�i%p�j�A���s���[�U�i%u�j�A���s�O���[�v�i%g�j�A�����O���[�v�i%G�j�A�����[���i%y�j�A�R�}���h�i%c�j�ƂȂ��Ă��܂��B���s�����̂̓��[�Usato�ł����AsetGID����Ă��邽��tty�O���[�v�Ƃ��ē��삵�Ă��邱�Ƃ��m�F�ł��܂��B

tty�Ƃ́uTele-TYpewriter�v�̈Ӗ��ŁA�[����\���܂��Bwrite�R�}���h�̓��O�C�����Ă��鑼�̃��[�U�̒[���Ƀ��b�Z�[�W��\�����邽�߂�setGID���s���Ď����O���[�v��tty�O���[�v�ɂ��Ă���킯�ł��B

### �X�e�B�b�L�[�r�b�g
�X�e�B�b�L�[�r�b�g���ݒ肳�ꂽ�t�@�C����f�B���N�g���́A�u���ׂẴ��[�U���������߂邪�A���L�҂����폜�ł��Ȃ��v�Ƃ����A�N�Z�X�������ݒ肳��܂��B

���Ƃ���/tmp�f�B���N�g���ɑ΂��ăX�e�B�b�L�[�r�b�g���ݒ肳��Ă��܂��B/tmp�f�B���N�g���͑S�Ẵ��[�U��A�v���P�[�V�������������߂�f�B���N�g���Ƃ��āA�ꎞ�t�@�C���̍쐬�ȂǂɎg�p����Ă��܂��B������/tmp�f�B���N�g���̃p�[�~�b�V������777�irwxrwxrwx�j�ɐݒ肷��ƁA�쐬�����t�@�C���𑼂̃��[�U���폜�ł��Ă��܂��܂��B������/tmp�f�B���N�g���ɃX�e�B�b�L�[�r�b�g��ݒ肷��ƁA���̃t�@�C�����폜�ł���͍̂쐬�������[�U�݂̂ƂȂ�܂��B

�X�e�B�b�L�[�r�b�g���ݒ肳��Ă���ƁAls�R�}���h�̏o�͂ł��̑��̃��[�U�̎��s�p�[�~�b�V�������ut�v�ƕ\������܂��B

```shell-session
[sato@server ~]$ ls -ld /tmp
drwxrwxrwt. 16 root root 4096  1�� 14 20:26 2015 /tmp
```

���[�Usato��/tmp/sbittest���쐬���A�p�[�~�b�V������666�ɐݒ肵�܂��B

```shell-session
[sato@server ~]$ touch /tmp/sbittest
[sato@server ~]$ chmod 666 /tmp/sbittest 
[sato@server ~]$ ls -l /tmp/sbittest 
-rw-rw-rw-. 1 sato sato 0  1�� 14 20:28 2015 /tmp/sbittest
```

���[�Usuzuki��/tmp/sbittest�ɏ������݂����܂��B���̑��̃��[�U�[�ɑ΂��鏑�����݂̃p�[�~�b�V�������t�^����Ă���̂ŏ������݂��s���܂��B

```shell-session
[suzuki@server ~]$ echo "suzuki" >> /tmp/sbittest
[suzuki@server ~]$ cat /tmp/sbittest
suzuki
```

���[�Usuzuki��/tmp/sbittest���폜���悤�Ƃ��܂����A�X�e�B�b�L�[�r�b�g�������č폜�ł��܂���B

```shell-session
[suzuki@server ~]$ rm /tmp/sbittest 
rm: cannot remove `/tmp/sbittest': ������Ă��Ȃ�����ł�
```

���[�Usato��/tmp/sbittest���폜���܂��B���L���[�U�͍폜���s���܂��B

```shell-session
[sato@server ~]$ rm /tmp/sbittest
```

## POSIX ACL
ACL(Access Control List�BPOSIX������ACL�̂��߁APOSIX ACL�Ƃ��Ă΂��)�́ALinux�J�[�l��2.6����W���̗p����Ă���A�]����Linux�ł̃A�N�Z�X���������ׂ��ɃA�N�Z�X������ݒ�ł���Z�p�ł��B
Linux�ȊO��OS�A���Ƃ���Windows�Ȃǂł�ACL���T�|�[�g���Ă���A�t���ł��錠���̎�ނ����ׂ₩�Ȃ��̂ɂȂ��Ă��܂��BLinux�ł��AWindows�����̃t�@�C���T�[�o�Ƃ���Samba�𗘗p����ꍇ�Ȃǂɂ́A���l�̃A�N�Z�X�����ݒ���s�����߂�ACL���K�v�ł��B

### ACL��L���ɂ�������Ɗm�F
ACL�̓t�@�C���V�X�e���̊g�������𗘗p���Ă��邽�߁A�g���������T�|�[�g����Ă���t�@�C���V�X�e����p����K�v������܂��Bext3��ext4�AXFS�ȂǂقƂ�ǂ̃t�@�C���V�X�e���ł͊g���������T�|�[�g����Ă��܂��B
�܂��A�t�@�C���V�X�e���ɂ���Ă̓}�E���g����ۂ�mount�R�}���h��acl�I�v�V�������w�肷��K�v������܂����ACentOS 6�ŕW���ŗ��p���Ă���ext4�ł̓f�t�H���g��ACL���L���ɂȂ��Ă���̂ŁAacl�I�v�V�����̎w��͕K�v����܂���B

ACL���g�p�ł��邩�́Als�R�}���h�Ńp�[�~�b�V�������m�F�������ɁA�p�[�~�b�V�����̍Ō��"."���\������Ă��邱�ƂŔ��ʂł��܂��B

"."�́A���̃t�@�C����ACL���ݒ肳��Ă��Ȃ����Ƃ��Ӗ����Ă��܂��BACL���ݒ肳����"+"�ɕ\�����ύX����܂��B

### ACL�̐ݒ��
���ۂ�ACL��ݒ肵�Ă݂܂��Bgetfacl�R�}���h�̓t�@�C����f�B���N�g���ɑ΂��āA�ݒ肳��Ă���ACL��\������R�}���h�ł��B�܂��Asetfacl�̓t�@�C����f�B���N�g���ɑ΂��āAACL��ݒ肷��R�}���h�ł��B

���[�Usato��/tmp/acltest�t�@�C�����쐬���܂��B

```shell-session
[sato@server ~]$ touch /tmp/acltest
```

getfacl�R�}���h��/tmp/acltest�t�@�C����ACL���m�F���܂��B

```shell-session
[sato@server ~]$ getfacl /tmp/acltest
getfacl: Removing leading '/' from absolute path names
# file: tmp/acltest
# owner: sato
# group: sato
user::rw-
group::r--
other::r--
```

���[�Usuzuki��/tmp/acltest�t�@�C���ɏ������݂����܂��B���̑��̃��[�U�ɂ̓p�[�~�b�V�������t�^����Ă��Ȃ��̂ŏ������݂��s���܂���B

```shell-session
[suzuki@server ~]$ echo "suzuki" >> /tmp/acltest
-bash: /var/tmp/acltest: ��������܂���
```

���[�Usato��setfacl�R�}���h�����s���āA���[�Usuzuki��/tmp/acltest�ɑ΂���ǂݏ�����ACL��ݒ肵�܂��B

```shell-session
[sato@server ~]$ setfacl -m u:suzuki:rw /tmp/acltest 
[sato@server ~]$ getfacl /tmp/acltest 
getfacl: Removing leading '/' from absolute path names
# file: tmp/acltest
# owner: sato
# group: sato
user::rw-
��user:suzuki:rw- ���[�Usuzuki�ɑ΂���ACL���ݒ肳��Ă���
group::rw-
mask::rw-
other::r--
```

���[�Usuzuki�ōēx/tmp/acltest�t�@�C���ɏ������݂����܂��BACL���ݒ肳�ꂽ�̂ŏ������݂��s���܂��B

```shell-session
[suzuki@server ~]$ echo "suzuki" >> /tmp/acltest
[suzuki@server ~]$ cat /tmp/acltest 
suzuki
```

���[�Usato��setfacl�R�}���h�����s���āA���[�Usuzuki��/tmp/acltest�ɑ΂���ǂݏ�����ACL���폜���܂��B

```shell-session
[sato@server ~]$ setfacl -x u:suzuki /tmp/acltest 
[sato@server ~]$ getfacl /tmp/acltest
getfacl: Removing leading '/' from absolute path names
# file: tmp/acltest
# owner: sato
# group: sato
user::rw-
group::rw-
mask::rw-
other::r--
```

���[�Usuzuki��/tmp/acltest�t�@�C���ɍēx�������݂����܂��BACL���폜���ꂽ�̂ŏ������݂��s���܂���B

```shell-session
[suzuki@server ~]$ echo "suzuki" >> /tmp/acltest
-bash: /var/tmp/acltest: ��������܂���
```

### Samba��ACL�̊֌W
Samba��Windows�N���C�A���g�ɑ΂��ăt�@�C�����L��񋟂����ۂɁAWindows�Őݒ肵���ׂ��Ȍ�����Linux��ł�ACL��p���Ď�������Ă��܂��B

��Ƃ��āA/home/sato�ȉ���samba_ACL_test�f�B���N�g�����쐬���AACL�̐ݒ���s���Ă݂܂��B

#### Samba�̃C���X�g�[���Ɛݒ�
Samba���C���X�g�[�����܂��B

```shell-session
# yum install samba
```

Samba�̐ݒ�t�@�C��/etc/samba/smb.conf��workgroup�ݒ��ύX���܂��B���[�N�O���[�v����Windows�N���C�A���g�̎Q�����Ă��郏�[�N�O���[�v�ɍ��킹�܂��BWindows�N���C�A���g�̃f�t�H���g�̃��[�N�O���[�v��WORKGROUP�ł��B

```shell-session
vi /etc/samba/smb.conf

        workgroup = ��WORKGROUP �����[�N�O���[�v����ύX��
```

Samba���N�����܂��Bsmb�T�[�r�X��nmb�T�[�r�X���N�����܂��B

```shell-session
# service smb start
SMB �T�[�r�X���N����:                                      [  OK  ]
# service nmb start
NMB �T�[�r�X���N����:                                      [  OK  ]
```

#### iptables�̐ݒ�ύX
iptables�̐ݒ��ύX���܂��Bsystem-config-firewall-tui�R�}���h�����s���ăJ�X�^�}�C�Y�ݒ��Samba�������邩�A/etc/sysconfig/iptables�Ɉȉ���4�s��ݒ肵��iptables�T�[�r�X��reload���܂��BSamba�̎g�p���Ă���SMB/CIFS�v���g�R����TCP��UDP��2��ނł���_�ɒ��ӂ��Ă��������B

```shell-session
-A INPUT -m state --state NEW -m udp -p udp --dport 137 -j ACCEPT
-A INPUT -m state --state NEW -m udp -p udp --dport 138 -j ACCEPT
-A INPUT -m state --state NEW -m tcp -p tcp --dport 139 -j ACCEPT
-A INPUT -m state --state NEW -m tcp -p tcp --dport 445 -j ACCEPT
```

#### SELinux�̐ݒ�ύX
SELinux���L���ȏꍇ�ASELinux�̐ݒ��ύX���܂��B�ȉ���setsebool�R�}���h�����s���āASamba�o�R�Ń��[�U�̃z�[���f�B���N�g���ւ̃A�N�Z�X�������܂��BSELinux�̐ݒ�ɂ��Ă͌�q���܂��B

```shell-session
# setsebool -P samba_enable_home_dirs on
```

#### Samba���[�U�̓o�^
smbpasswd�R�}���h��Samba���[�U��o�^���܂��B���[�U�A�J�E���g�͂��炩����Linux�ɓo�^����Ă��郆�[�U�A�J�E���g���w�肷��K�v������܂��B�����ł̓��[�Usato���w�肵�Ă��܂��B���͂����p�X���[�h�́AWindows�N���C�A���g����t�@�C�����L�փA�N�Z�X����ۂ̔F�؂Ɏg�p���܂��B

```shell-session
# smbpasswd -a sato
New SMB password: ���p�X���[�h�����
Retype new SMB password: ���p�X���[�h���ē���
Added user sato.
```

#### Windows�N���C�A���g����Samba�ւ̃A�N�Z�X
Windows�N���C�A���g����Samba�̃t�@�C�����L�ɃA�N�Z�X���܂��B

1. Samba�ւ̃A�N�Z�X���w�肵�܂��B

![Samba�ւ̃A�N�Z�X](samba0.png)

�u�X�^�[�g�v�{�^�����u�v���O�����ƃt�@�C���̌����v�Ɂu\\server\�v�A���邢�́u\\192.168.0.10�v�Ɠ��͂��܂��B

��2

2. ���[�U�F�؂��s���܂��B

![���[�U�F��](samba1.png)

���[�U�F�؂��v�����ꂽ�ꍇ�ɂ́A�O�̎菇�œo�^�������[�U���A�p�X���[�h�ŔF�؂��s���܂��B

��3

3. ���[�U�z�[�����L�ɃA�N�Z�X���܂��B

![���[�U�z�[�����L](samba2.png)

���[�U�A�J�E���g���̃t�@�C�����L�isato�j�̃A�C�R�����_�u���N���b�N�ŊJ���܂��B�����Samba�����[�U�̃z�[���f�B���N�g���������I�ɋ��L�Ƃ��Ĉ����A���[�U�z�[�����L�̋@�\���g���Ă��܂��B

��4

4. �e�X�g�p�̃t�H���_���쐬���܂��B

![samba_acl_test�t�H���_](samba3.png)

samba_acl_test�t�H���_���쐬���܂��B

��5

5. �t�H���_�̃v���p�e�B�E�C���h�E���Ăяo���܂��B

![�v���p�e�B](samba4.png)

Windows�N���C�A���g��samba_acl_test�t�H���_���E�N���b�N���āA�u�v���p�e�B�v��I�����܂��B�u�Z�L�����e�B�v�^�u���N���b�N���āA�u�ڍאݒ�v�{�^�����N���b�N���܂��B

��6

6. �A�N�Z�X���G���g�����m�F���܂��B

![�ǂݏ����̂�](samba5.png)

�uEveryone�v���_�u���N���b�N���āA�u���v��5�`�F�b�N����Ă��邱�Ƃ��m�F���܂��B�uOK�v�{�^�����N���b�N���܂��B�����OK�{�^�����N���b�N���āA�v���p�e�B�̃E�C���h�E�ɖ߂�܂��B

#### Linux����ACL���m�F
1. ���[�Usato�Ń��O�C�����A�z�[���f�B���N�g���ɍ��ꂽsamba_acl_test�f�B���N�g����ACL���m�F���܂��B

```shell-session
[sato@server ~]$ getfacl samba_acl_test/
# file: samba_acl_test/
# owner: sato
# group: sato
user::rwx
group::r-x
other::r-x
```

��2

2. setfacl�R�}���h�����s���āAsamba_acl_test�f�B���N�g���ɑ΂��āA���̑��̃��[�U�ɏ������݂�ACL��t�^���܂��B

```shell-session
[sato@server ~]$ setfacl -m o::rwx samba_acl_test
[sato@server ~]$ getfacl samba_acl_test/
# file: samba_acl_test/
# owner: sato
# group: sato
user::rwx
group::r-x
other::r��w��x �����������݌������t�^����Ă���
```

��3

3. Windows�N���C�A���g�ōēx�A�N�Z�X���G���g�����m�F���܂��B

![���ׂẴA�N�Z�X����](samba5.png)

Windows�N���C�A���g�ōēx�u�ڍאݒ�v�{�^�����N���b�N���܂��B�uEveryone�v���_�u���N���b�N���āA���ׂẴA�N�Z�X�����ڂ��`�F�b�N����Ă��邱�Ƃ��m�F���܂��B

## SELinux
SELinux��Linux�J�[�l��2.6����������ꂽ�Aroot���[�U�̓����ɑ΂��Ă��������|���邱�Ƃ��ł��鋭���A�N�Z�X����iMAC�AMandatory Access Control�j�̎d�g�݂ł��B

�{���ȏ��ł́ASELinux�̊�{�I�ȊǗ��ɂ��ĉ�����܂��BSELinux�̂��ڂ��������ɂ��ẮA�wLinux�Z�L�����e�B�W�����ȏ��x���Q�Ƃ��Ă��������B

### SELinux�̎d�g��
SELinux�ł́A�v���Z�X��t�@�C���Ȃ�Linux�̑S�Ẵ��\�[�X�ɑ΂��āu�R���e�L�X�g�v�icontexts�j�ƌĂ΂�郉�x����t�����A�u�T�u�W�F�N�g�v�isubject�B�A�N�Z�X���鑤�B��Ƀv���Z�X�j���u�I�u�W�F�N�g�v�iobject�B�A�N�Z�X����鑤�B��Ƀt�@�C����f�B���N�g���A�v���Z�X�j�ɑ΂��ăA�N�Z�X���s���ۂɁA���̃R���e�L�X�g���r���邱�Ƃɂ��A�N�Z�X������s���܂��B

�����̃R���e�L�X�g��g�ݍ��킹�āA�A�N�Z�X�̉ۂ��s�����[����SELinux�ł́u�|���V�[�v�ƌĂт܂��B�|���V�[�̏ڍׂȐ����ƏC���Ɋւ��ẮA�wLinux�Z�L�����e�B�W�����ȏ��x���Q�Ƃ��Ă��������B

### SELinux�̗L���A�����̊m�F
SELinux�̏�Ԃ�getenforce�R�}���h�Ŋm�F�ł��܂��B

```shell-session
[root@server ~]# getenforce 
Enforcing
```

getenforce�R�}���h�̌��ʂ͈ȉ��̒ʂ�ł��B

|����|���|
|-------|-------|
|Enforcing|SELinux�ɂ��A�N�Z�X���䂪�L��|
|Permissive|SELinux�͗L���ł��邪���싑�ۂ͍s��Ȃ�|
|Disabled|SELinux�ɂ��A�N�Z�X���䂪����|

SELinux�̏�Ԃ́Asetenforce�R�}���h�ɂ�铮�I�ȕύX���A�ݒ�t�@�C��/etc/selinux/config�ɂ��ÓI�ȕύX�̂����ꂩ�ŕύX�ł��܂��B

### setenforce�R�}���h�ɂ��SELinux�̓��I�ȕύX
setenforce�R�}���h��SELinux�̏�Ԃ𓮓I�ɕύX�ł��܂��B�ύX��root���[�U�Ŏ��s����K�v������܂��B

�������A���I�ɕύX�ł���̂�Enforcing��Permissive�̐؂�ւ��݂̂ŁASELinux��L�����疳���iDisabled�j�ɁA���邢�͖�������L���ɕύX���邱�Ƃ͂ł��܂���B
�L���A�����̐؂�ւ��́A��q����ݒ�t�@�C���ɂ��ÓI�ȕύX�ƃV�X�e���̍ċN�����K�v�ł��B

```
setenforce [ Enforcing | Permissive | 1 | 0 ]
```

���Ƃ��΁A�V�X�e����SELinux�ɂ��A�N�Z�X������ꎞ�I�ɓK�p���Ȃ��悤�ɂ������Ƃ��ɂ͏�Ԃ�Permissive�ɕύX���܂��BSELinux�ɂ��A�N�Z�X����ł̓���̋��ۂ͍s���Ȃ��Ȃ�܂����A�f�o�b�O�Ȃǂ̗p�r�̂��߂�SELinux�̃|���V�[�ᔽ����������ƃ��O�͏o�͂���܂��B
�V�X�e�����v�����悤�ɓ��삹���ASELinux�������Ǝv���鎞�Ȃǂ�Permissive�ɐݒ肵�āASELinux���������ǂ����̐؂蕪����Ƃ��s���܂��B

```shell-session
# setenforce permissive
# getenforce 
Permissive
```

### SELinux�̖�����
SELinux�𖳌��ɂ���A���邢�͖�������L���ɕύX����ɂ�SELinux�̐ݒ�t�@�C��/etc/selinux/config�̐ݒ��ύX���܂��B�V�X�e�����ċN������ƁA�ݒ肪���f����܂��B

/etc/selinux/config��ҏW���A�ݒ荀��SELINUX�̒l��disabled�ɕύX���܂��B

```shell-session
# vi /etc/selinux/config

��#��SELINUX=enforcing �����s����#��ǉ�
��SELINUX=disabled ���V���ɒǉ�
```

�V�X�e�����ċN�����܂��B

```shell-session
# reboot
```

getenforce�R�}���h��SELinux�������iDisabled�j�ɂȂ������Ƃ��m�F���܂��B

```shell-session
# getenforce
Disabled
```

/etc/selinux/config��ҏW���A�ݒ荀��SELINUX�̒l��enforcing�ɕύX���܂��B

```shell-session
# vi /etc/selinux/config

SELINUX=enforcing �����s����#���폜
��#��SELINUX=disabled �����s����#��ǉ�
```

�V�X�e�����ċN�����܂��B

```shell-session
# reboot
```

getenforce�R�}���h��SELinux���L���iEnforcing�j�ɂȂ������Ƃ��m�F���܂��B

```shell-session
# getenforce
Enforcing
```

### �R���e�L�X�g�̊m�F
�R���e�L�X�g�̓t�@�C���Ȃǂɐݒ肳��A�A�N�Z�X����ɗ��p����܂��B�R���e�L�X�g�́A����4�̎��ʎq�ō\������Ă��܂��B

* ���[�U(user)
* ���[��(role)
* �^�C�v(type)�F�v���Z�X�̏ꍇ�ɂ͓��Ɂu�h���C���v�Ƃ������܂�
* MLS�F���x��Multi Level Security��񋟂ł��܂����A�ʏ�̃V�X�e���ł͂��܂�g���܂���

�R���e�L�X�g�́A�����̎��ʎq��g�ݍ��킹�āA�ȉ��̌`���ŕ\����܂��B

```
���[�U:���[��:�^�C�v:MLS���x��
```

SELinux�ł̃A�N�Z�X����́A�^�C�v�^�h���C���ɑ΂��ċ����铮����`�����u�|���V�[�v�Ɋ�Â��čs���܂��B�^�C�v�^�h���C���̖��O�́A������v���Z�X����������Ă��܂��B���Ƃ��΁AApache Web�T�[�o�̃v���Z�X�ł���httpd�ɂ́uhttpd_t�v�Ƃ����h���C���������Ă��܂��B

### �R���e�L�X�g�̊m�F
SELinux�̃A�N�Z�X����ŗp������R���e�L�X�g�́A�v���Z�X��t�@�C�����Q�Ƃ���R�}���h��-Z�I�v�V���������Ď��s���邱�ƂŊm�F�ł��܂��B

���Ƃ��΁A�t�@�C����f�B���N�g���ɕt�^����Ă���R���e�L�X�g���m�F����ɂ�ls -lZ�R�}���h�����s���܂��B��Ƃ��āAApache Web�T�[�o�ihttpd�j�Ɋւ���t�@�C�����m�F���Ă݂܂��B

```shell-session
# ls -lZ /var/www
drwxr-xr-x. root root system_u:object_r:httpd_sys_script_exec_t:s0 cgi-bin
drwxr-xr-x. root root system_u:object_r:httpd_sys_content_t:s0 error
drwxr-xr-x. root root system_u:object_r:httpd_sys_content_t:s0 html
drwxr-xr-x. root root system_u:object_r:httpd_sys_content_t:s0 icons
```

/var/www/html�f�B���N�g����/var/www/icons�f�B���N�g���ȂǁAWeb�T�[�o�̃R���e���c���܂ރf�B���N�g���ɂ́uhttpd_sys_content_t�v�Ƃ����^�C�v���t�^����Ă��܂��B����/var/www/html�f�B���N�g�����Ƀt�@�C�����쐬����ƁA�e�f�B���N�g���̃R���e�L�X�g�ɏ]���ăt�@�C���ɃR���e�L�X�g���t�^����܂��B

�m�F�̂��߂ɁA/var/www/html�f�B���N�g���ȉ���index.html�t�@�C�����쐬���Ă݂܂��B
�e�f�B���N�g������R���e�L�X�g���p�����Aindex.html�t�@�C���Ɂuhttpd_sys_content_t�v�Ƃ����^�C�v���t�^����Ă��܂��B

```shell-session
# touch /var/www/html/index.html 
# ls -lZ /var/www/html/index.html 
-rw-r--r--. root root unconfined_u:object_r:��httpd_sys_content_t��:s0 /var/www/html/index.html
```

�܂��A�v���Z�X�̃R���e�L�X�g�̏����m�F����ɂ́Aps axZ�R�}���h�����s���܂��B

�ȉ��̗�ł́Ahttpd�̃v���Z�X���m�F����ƁAhttpd_t�h���C�����t�^����Ă��邱�Ƃ�������܂��B

```shell-session
[root@server ~]# service httpd start
httpd ���N����:                                            [  OK  ]
[root@server ~]# ps axZ | grep httpd
unconfined_u:system_r:httpd_t:s0 27104 ?       Ss     0:00 /usr/sbin/httpd
unconfined_u:system_r:httpd_t:s0 27106 ?       S      0:00 /usr/sbin/httpd
�i���j
```

SELinux�̃|���V�[�ł́Ahttpd�v���Z�X�ɕt�^����Ă���httpd_t�h���C�����A�uhttpd_sys_content_t�v�Ȃǂ̃^�C�v���t�^����Ă���t�@�C����read�i�ǂݎ��j�Ȃǂ��s����悤�Ɍ������ݒ肳��Ă��܂��B

### Boolean���g����SELinux�̐���
SELinux��L���ɂ��ăA�v���P�[�V���������܂����삵�Ȃ��ꍇ�ɂ́ASELinux�̃A�N�Z�X����ɂ���ăv���Z�X���t�@�C����f�B���N�g���ɃA�N�Z�X�ł��Ȃ����Ƃ������̏ꍇ������܂��B���̂悤�Ȏ��ɂ́ASELinux�̃|���V�[��ݒ肷��K�v������܂��B

��ʓI�ȃ|���V�[�̐ݒ�́uBoolean�v�i�u�[���A���j�ƌĂ΂��ݒ�̗L���A�����őΉ��ł��܂��BBoolean�Őݒ�ł��鍀�ڂ́ACentOS 6�ł́A200��قǂ���܂��B

�����A�Ǝ��̃A�v���P�[�V�������g�p������A�A�v���P�[�V�����̐ݒ��啝�ɕύX�����ꍇ�ɂ́A�|���V�[��ǉ��A�C������K�v������܂��B�|���V�[�̒ǉ��A�C�����@�ɂ��ẮwLinux�Z�L�����e�B�W�����ȏ��x���Q�Ƃ��Ă��������B

�ȉ��̗�ł́AApache Web�T�[�o(httpd)�Ɋւ���|���V�[��ݒ肵�Ă��܂��B

getsebool�R�}���h��Boolean�̐ݒ�󋵈ꗗ���m�F���܂��BBoolean���ɂ͊֌W����v���Z�X�����܂܂�Ă���̂ŁAgrep�R�}���h�Łuhttpd�v���L�[���[�h�ɂ��Č������܂��B

```shell-session
# getsebool -a | grep httpd
allow_httpd_anon_write --> off
allow_httpd_mod_auth_ntlm_winbind --> off
�i���j
httpd_enable_homedirs --> off
�i���j
```

��̍�Ƃ�httpd_enable_homedirs��Boolean��ݒ肵�܂��B����Boolean�́AApache Web�T�[�o�̃��[�U�z�[���f�B���N�g���@�\�Ɋւ���ݒ�ł��B���[�U�z�[���f�B���N�g���@�\�́A�e���[�U�̃z�[���f�B���N�g���ɍ쐬���ꂽpublic_html�f�B���N�g������Web�R���e���c�Ƃ��Č��J����d�g�݂ł��B

Apache Web�T�[�o�̐ݒ�t�@�C��/etc/httpd/conf/httpd.conf���C�����AUserDir�f�B���N�e�B�u��ݒ肵�ă��[�U�z�[���f�B���N�g���@�\��L���ɂ��܂��B

```shell-session
# vi /etc/httpd/conf/httpd.conf

�i���j
<IfModule mod_userdir.c>
    #
    # UserDir is disabled by default since it can confirm the presence
    # of a username on the system (depending on home directory
    # permissions).
    #
    ��#��UserDir disabled �����s����#��ǉ�

    #
    # To enable requests to /~user/ to serve the user's public_html
    # directory, remove the "UserDir disabled" line above, and uncomment
    # the following line instead:
    #
    UserDir public_html �����s����#���폜
�i���j
```

httpd�T�[�r�X���ċN�����܂��B

```shell-session
# service httpd restart
httpd ���~��:                                            [  OK  ]
httpd ���N����:                                            [  OK  ]
```

���[�Usato�Ń��O�C�����A�z�[���f�B���N�g����public_html�f�B���N�g�����쐬���܂��B

```shell-session
$ pwd
/home/sato
$ mkdir public_html
```

/home/sato�f�B���N�g���A/home/sato/public_html�f�B���N�g���̃p�[�~�b�V������711�ɐݒ肵�܂��B

```shell-session
$ chmod 711 /home/sato
$ chmod 711 /home/sato/public_html/
```

public_html�f�B���N�g����index.html�t�@�C�����쐬���܂��B

```shell-session
[sato@server ~]$ echo "SELinux test" > /home/sato/public_html/index.html
```

�u���E�U���N�����A�uhttp://192.168.0.10/~sato/�v�ɃA�N�Z�X���܂��BSELinux�̃A�N�Z�X���䂪�L���ɂȂ��Ă��邽�߁A�uForbidden�v���\������܂��B

![Forbidden](Forbidden.png)

root���[�U�Ń��O�t�@�C��/var/log/audit/audit.log���m�F���܂��Bhttpd(httpd_t)�����[�U�z�[���f�B���N�g��(user_home_dir_t)�ɃA�N�Z�X�ł��Ȃ������Ƃ������O���o�͂���Ă��܂��B

```shell-session
[root@server ~]# tail /var/log/audit/audit.log 
�i���j
type=AVC msg=audit(1421241819.317:804): avc:  ��denied  { search }�� for  pid=7357 comm="httpd" name="sato" dev=dm-2 ino=130305 scontext=unconfined_u:system_r:��httpd_t��:s0 tcontext=unconfined_u:object_r:��user_home_dir_t��:s0 tclass=dir
type=SYSCALL msg=audit(1421241819.317:804): arch=c000003e syscall=4 success=no exit=-13 a0=7f7f0adf26e8 a1=7fff803d37c0 a2=7fff803d37c0 a3=1999999999999999 items=0 ppid=7352 pid=7357 auid=0 uid=48 gid=48 euid=48 suid=48 fsuid=48 egid=48 sgid=48 fsgid=48 tty=(none) ses=87 comm="httpd" exe="/usr/sbin/httpd" subj=unconfined_u:system_r:��httpd_t��:s0 key=(null)
type=AVC msg=audit(1421241819.317:805): avc:  ��denied  { getattr }�� for  pid=7357 comm="httpd" ��path="/home/sato"�� dev=dm-2 ino=130305 scontext=unconfined_u:system_r:��httpd_t��:s0 tcontext=unconfined_u:object_r:��user_home_dir_t��:s0 tclass=dir
type=SYSCALL msg=audit(1421241819.317:805): arch=c000003e syscall=6 success=no exit=-13 a0=7f7f0adf2798 a1=7fff803d37c0 a2=7fff803d37c0 a3=1 items=0 ppid=7352 pid=7357 auid=0 uid=48 gid=48 euid=48 suid=48 fsuid=48 egid=48 sgid=48 fsgid=48 tty=(none) ses=87 comm="httpd" exe="/usr/sbin/httpd" subj=unconfined_u:system_r:��httpd_t��:s0 key=(null)
```

setsebool�R�}���h�����s���āABoolean�uhttpd_enable_homedirs�v��L���ɐݒ肵�܂��B

```shell-session
[root@server ~]# getsebool httpd_enable_homedirs
httpd_enable_homedirs --> off
[root@server ~]# setsebool httpd_enable_homedirs on
[root@server ~]# getsebool httpd_enable_homedirs
httpd_enable_homedirs --> on
```

�ēx�u���E�U�Łuhttp://192.168.0.10/~sato/�v�ɃA�N�Z�X���܂��BBoolean�ŃA�N�Z�X�������ꂽ�̂ŁA�쐬�����y�[�W���\������܂��B

## LVM�̐ݒ�
LVM�iLogical Volume Manager�j�́A�n�[�h�f�B�X�N�Ȃǂ̋L���}�̂̕����I�ȏ�Ԃ��B�����A�_���I�ȃC���[�W�ŊǗ����邽�߂̋Z�p�ł��B

LVM���g�����ƂŁA�����̃n�[�h�f�B�X�N�ɂ܂��������{�����[�����쐬�ł���悤�ɂȂ�A�t�@�C���V�X�e���̗e�ʂ�����Ȃ��Ȃ����ꍇ�̗e�ʂ̒ǉ����ȒP�ɂȂ�܂��B�{�����[���̑���́A�V�X�e�����ċN�����邱�ƂȂ��s�����Ƃ��ł��܂��B

�܂��A�n�[�h�f�B�X�N�ɏ�Q�������������ɂ́A�V����HDD��ǉ����āA���Ă���HDD���O���Ȃǂ̏�Q�Ή����e�ՂɂȂ�܂��B
���ɂ��A�X�i�b�v�V���b�g����邱�Ƃ��ł���Ȃǂ̃����b�g������܂��B

���݂̈�ʓI��Linux�f�B�X�g���r���[�V�����ł́A�C���X�g�[������LVM�Ńp�[�e�B�V�������쐬�ł��܂��BCentOS�ł́A�C���X�g�[�����Ɏ����p�[�e�B�V�����ݒ��I������ƁA�f�t�H���g��LVM���g�p���ăX�g���[�W��ݒ肵�܂��B

LVM�̏ڂ��������Ɋւ��ẮA�w���M���V�X�e���\�z�W�����ȏ��x���Q�Ƃ��Ă��������B

LVM�́A�����{�����[���iPV: Physical Volume�j�A�{�����[���O���[�v�iVG: Volume Group�j�A�_���{�����[���iLV: Logical Volume�j��3�ō\������Ă��܂��B

### �����{�����[���iPV�j
�����{�����[��(PV)�́A�����f�B�X�N�̃p�[�e�B�V�����P�ʂň����܂��B��̕����f�B�X�N���ׂĂ����PV�Ƃ��Ĉ������Ƃ��ł��܂����A��̕����f�B�X�N���Ƀp�[�e�B�V�����𕡐��쐬���A���ꂼ��̃p�[�e�B�V������ʁX��PV�Ƃ��Ĉ������Ƃ��ł��܂��B

PV���쐬����ɂ́A�p�[�e�B�V�������쐬���A�p�[�e�B�V�����^�C�v��8E�ɐݒ肵�܂��B

�ȉ��̗�ł́ALinux�}�V���ɐV�K�ɒǉ�����/dev/sdb�Ƃ��ĔF������Ă���n�[�h�f�B�X�N��LVM�Ŏg�p�ł���悤�Afdisk�Ńp�[�e�B�V�������쐬����PV�Ƃ��Đݒ肵�Ă��܂��B�����ɁA��̍�Ƃŗ̈�g�����s�����߂̒ǉ��p�[�e�B�V�������쐬���Ă����܂��B

```shell-session
# fdisk /dev/sdb
�f�o�C�X�͐���� DOS �̈�e�[�u�����ASun, SGI �� OSF �f�B�X�N���x����
�܂�ł��܂���
�i���j

�R�}���h (m �Ńw���v): ��n ���V�K�p�[�e�B�V�����쐬��n�����
�R�}���h�A�N�V����
   e   �g��
   p   ��{�p�[�e�B�V���� (1-4)
��p ����{�p�[�e�B�V������p�����
�p�[�e�B�V�����ԍ� (1-4): ��1 ���p�[�e�B�V�����ԍ�1�����
�ŏ� �V�����_ (1-8354, �����l 1): ��1 ���p�[�e�B�V�����ԍ�1�����
Last �V�����_, +�V�����_�� or +size{K,M,G} (1-8354, �����l 8354): ��+2G ���e�ʂƂ���+2GB�����

�R�}���h (m �Ńw���v): ��n ���V�K�p�[�e�B�V�����쐬��n�����
�R�}���h�A�N�V����
   e   �g��
   p   ��{�p�[�e�B�V���� (1-4)
��p ����{�p�[�e�B�V������p�����
�p�[�e�B�V�����ԍ� (1-4): ��2 ���p�[�e�B�V�����ԍ�2�����
�ŏ� �V�����_ (263-8354, �����l 263): ��Enter�L�[�����
�����l 263 ���g���܂�
Last �V�����_, +�V�����_�� or +size{K,M,G} (263-8354, �����l 8354): ��+2G ���e�ʂƂ���+2GB�����

�R�}���h (m �Ńw���v): ��t ���p�[�e�B�V�����^�C�v�ύX��t�����
�p�[�e�B�V�����ԍ� (1-4): ��1 ���p�[�e�B�V�����ԍ�1�����
16�i���R�[�h (L �R�}���h�ŃR�[�h���X�g�\��): ��8e ��LVM�p��8e�����
�̈�̃V�X�e���^�C�v�� 1 ���� 8e (Linux LVM) �ɕύX���܂���

�R�}���h (m �Ńw���v): ��t ���p�[�e�B�V�����^�C�v�ύX��t�����
�p�[�e�B�V�����ԍ� (1-4): ��2 ���p�[�e�B�V�����ԍ�2�����
16�i���R�[�h (L �R�}���h�ŃR�[�h���X�g�\��): ��8e ��LVM�p��8e�����
�̈�̃V�X�e���^�C�v�� 2 ���� 8e (Linux LVM) �ɕύX���܂���

�R�}���h (m �Ńw���v): ��w ���p�[�e�B�V����������������w�����
�p�[�e�B�V�����e�[�u���͕ύX����܂����I

ioctl() ���Ăяo���ăp�[�e�B�V�����e�[�u�����ēǍ��݂��܂��B
�f�B�X�N�𓯊����Ă��܂��B
```

### �{�����[���O���[�v�iVG�j
�{�����[���O���[�v(VG)�́A1�ȏ�̕����{�����[���iPV�j���ЂƂ܂Ƃ߂ɂ������̂ł��B����͉��z�I�ȃf�B�X�N�ɑ������܂��B

�{�����[���O���[�v��vgcreate�R�}���h�ō쐬���܂��B

```
vgcreate �{�����[���� PV�f�o�C�X�� [PV�f�o�C�X�� ...]
```

���Ƃ��΁A�����{�����[���iPV�j�Ƃ��č쐬����/dev/sdb1���g����Volume00�Ƃ������O�̃{�����[���O���[�v���쐬����ɂ́A�ȉ���vgcreate�R�}���h�����s���܂��B

```shell-session
# vgcreate Volume00 /dev/sdb1
  Physical volume "/dev/sdb1" successfully created
  Volume group "Volume00" successfully created
```

�܂��A�{�����[���O���[�v�̏���vgscan�R�}���h�Ŋm�F�ł��܂��B

```shell-session
# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "Volume00" using metadata type lvm2
  Found volume group "vg_server" using metadata type lvm2
```

### �_���{�����[���iLV�j
�_���{�����[���iLV�j�́A�{�����[���O���[�v�iVG�j��ɍ쐬���鉼�z�I�ȃp�[�e�B�V�����ł��BLinux����̓f�o�C�X�Ƃ��ĔF������܂��B�n�[�h�f�B�X�N�ɕ����p�[�e�B�V�������쐬����ꍇ�Ɠ��l�ɁA�{�����[���O���[�v�����ׂĈ�̘_���{�����[���Ƃ��邱�Ƃ��ł��܂����A��̃{�����[���O���[�v�𕡐��̘_���{�����[���ɕ������Ďg�p���邱�Ƃ��ł��܂��B

�_���{�����[����lvcreate�R�}���h���g���č쐬���܂��B

```
lvcreate -L �T�C�Y -n �_���{�����[���� �{�����[���O���[�v��
```

���Ƃ��΁A�{�����[���O���[�vVolume00�ɃT�C�Y1GB�A�_���{�����[�����uLogVol01�v�̘_���{�����[�����쐬����ɂ́A�ȉ���lvcreate�R�}���h�����s���܂��B

```shell-session
# lvcreate -L 1024M -n LogVol01 Volume00
```

### �_���{�����[���Ƀt�@�C���V�X�e���̍쐬
�쐬�����_���{�����[���𗘗p����ɂ́A�ʏ�̃p�[�e�B�V�����Ɠ������_���{�����[����Ƀt�@�C���V�X�e�����쐬���܂��B�_���{�����[���́A�ȉ��̂悤�ȃf�o�C�X�Ƃ��Ĉ������Ƃ��ł��܂��B

```
/dev/�{�����[���O���[�v��/�_���{�����[����
```

/dev/Volume00/LogVol01���ext4�t�@�C���V�X�e�����쐬���邽�߂ɁAmkfs�R�}���h�����s���܂��B

```shell-session
# mkfs -t ext4 /dev/Volume00/LogVol01 
mke2fs 1.41.12 (17-May-2010)
Discarding device blocks: done                            
Filesystem label=
OS type: Linux
�i���j
This filesystem will be automatically checked every 33 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```

mount�R�}���h���g���āA/dev/Volume00/LogVol01���}�E���g���܂��B

```shell-session
# mkdir /mnt/LVMtest
# mount -t ext4 /dev/Volume00/LogVol01 /mnt/LVMtest/
# mount /mnt/LVMtest/
mount: /dev/mapper/Volume00-LogVol01 �� �}�E���g�ς� /mnt/LVMtest ���g�p���ł�
mount: mtab �ɂ��ƁA/dev/mapper/Volume00-LogVol01 �� /mnt/LVMtest �Ƀ}�E���g�ςł�
```

### �{�����[���O���[�v�ւ̃f�B�X�N�̒ǉ�
�����̃{�����[���O���[�vVolume00�ɕ����{�����[��/dev/sdb2��ǉ����܂��B

vgextend�R�}���h�����s���āA�����{�����[��/dev/sdb2���{�����[���O���[�vVolume00�ɒǉ����܂��B

```shell-session
# vgextend Volume00 /dev/sdb2
  Physical volume "/dev/sdb2" successfully created
  Volume group "Volume00" successfully extended
```

vgdisplay�R�}���h�����s���āA�{�����[���O���[�vVolume00�̏����m�F���܂��BPV�iPhysical volume�j�̐���2�ƂȂ��Ă���A/dev/sdb2��������Ă��邱�Ƃ�������܂��B

```shell-session
# vgdisplay Volume00
  --- Volume group ---
  VG Name               Volume00
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                ��2
  Act PV                ��2
  VG Size               4.01 GiB
  PE Size               4.00 MiB
  Total PE              1026
  Alloc PE / Size       256 / 1.00 GiB
  Free  PE / Size       770 / 3.01 GiB
  VG UUID               yTTwWd-G5tb-FzNb-Ow0L-ebvr-1n9I-ikLWo2
```

### �_���{�����[���̊g��
LVM�ł́A�_���{�����[���̃T�C�Y��ύX�ł��܂��B�܂��ALVM�̘_���{�����[����ɍ쐬���ꂽext4�t�@�C���V�X�e���́A�t�@�C���V�X�e�����}�E���g�����܂܊g���ł��܂��B

df�R�}���h�����s���āA���݂̃t�@�C���V�X�e���̗e�ʂ��m�F���܂��B���݂̗e�ʂ�1GB�ł��B

```shell-session
# df /mnt/LVMtest/
Filesystem           1K-blocks  Used Available Use% Mounted on
/dev/mapper/Volume00-LogVol01
                        999320  1284    945608   1% /mnt/LVMtest
```

lvextend�R�}���h�����s���āA�_���{�����[��LogVol01�̃T�C�Y��2G�܂Ŋg�債�܂��B

```shell-session
# lvextend -L 2G /dev/Volume00/LogVol01
 Size of logical volume Volume00/LogVol01 changed from 1.00 GiB (256 extents) to 2.00 GiB (512 extents).
  Logical volume LogVol01 successfully resized
```

resize2fs�R�}���h�����s���āA�t�@�C���V�X�e�����g�債�܂��B

```shell-session
# resize2fs /dev/Volume00/LogVol01
resize2fs 1.41.12 (17-May-2010)
Filesystem at /dev/Volume00/LogVol01 is mounted on /mnt/LVMtest; on-line resizing required
old desc_blocks = 1, new_desc_blocks = 1
Performing an on-line resize of /dev/Volume00/LogVol01 to 524288 (4k) blocks.
The filesystem on /dev/Volume00/LogVol01 is now 524288 blocks long.
```

df�R�}���h�ōēx�e�ʂ��m�F���܂��B�e�ʂ�2GB�ɑ����Ă��邱�Ƃ��m�F�ł��܂��B

```shell-session
# df /mnt/LVMtest/
Filesystem           1K-blocks  Used Available Use% Mounted on
/dev/mapper/Volume00-LogVol01
                       2031440  1536   1925060   1% /mnt/LVMtest
```

### �_���{�����[���̏k��
�^�p��A���̘_���{�����[�����g�債�������̗��R�Ŏg�p���̒Ⴂ�_���{�����[���̏k�����s���ꍇ������܂��B
�_���{�����[�����k������ɂ́A��Ƀt�@�C���V�X�e�����k�����A���̌�ɘ_���{�����[�����k������K�v������܂��B�t�@�C���V�X�e���̏k���̓}�E���g�����܂܂ł͍s���Ȃ��̂ŁA��ƒ��͈�x�A���}�E���g���Ă����K�v������܂��B

�k���������{�����[�����A���}�E���g���܂��Bumount�R�}���h�����s���āA/mnt/LVMtest���A���}�E���g���܂��B

```shell-session
# umount /mnt/LVMtest/
```

�k���������_���{�����[��/dev/Volume00/LogVol01�ɑ΂���fsck�R�}���h�����s���܂��B�����I�Ƀ`�F�b�N���s�����߂�-f�I�v�V������t�^���Ď��s���܂��B

```shell-session
# fsck -f /dev/Volume00/LogVol01 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/Volume00-LogVol01: 11/131072 files (0.0% non-contiguous), 16812/524288 blocks
```

resize2fs�R�}���h�����s���āA�t�@�C���V�X�e�����k�����܂��B��Ƃ��āA1GB�܂ŏk�����܂��B

```shell-session
# resize2fs /dev/Volume00/LogVol01 1G
resize2fs 1.41.12 (17-May-2010)
Resizing the filesystem on /dev/Volume00/LogVol01 to 262144 (4k) blocks.
The filesystem on /dev/Volume00/LogVol01 is now 262144 blocks long.
```

lvreduce�R�}���h�����s���āA�_���{�����[��/dev/Volume00/LogVol01���k�����܂��B

```shell-session
# lvreduce -L 1G /dev/Volume00/LogVol01
  WARNING: Reducing active logical volume to 1.00 GiB
  THIS MAY DESTROY YOUR DATA (filesystem etc.)
Do you really want to reduce LogVol01? [y/n]: ��y ��y�����
  Size of logical volume Volume00/LogVol01 changed from 2.00 GiB (512 extents) to 1.00 GiB (256 extents).
  Logical volume LogVol01 successfully resized
```

/mnt/LVMtest�ɍă}�E���g���āA�e�ʂ��m�F���܂��B

```shell-session
# mount -t ext4 /dev/Volume00/LogVol01 /mnt/LVMtest/
# df /mnt/LVMtest/
Filesystem           1K-blocks  Used Available Use% Mounted on
/dev/mapper/Volume00-LogVol01
                        999320  1284    945616   1% /mnt/LVMtest
```

## �o�b�N�A�b�v�^���X�g�A
�V�X�e�����^�p���Ă����ۂɂ́A�o�b�N�A�b�v�͏d�v�ł��B���ɏ�Q����V�X�e���𕜋�������Ƃ���A�d�v�ȃt�@�C��������č폜�����肷�郊�X�N���l����ƁA������ƃo�b�N�A�b�v�^���X�g�A�̃v�����𗧂ĂāA�O�����ăe�X�g�����Ă������Ƃ��d�v�ł��B

### �o�b�N�A�b�v���f�B�A�ɂ���
�ŋ߂̃X�g���[�W�̑�e�ʉ����l����ƁA�V�X�e���Ƃ͕ʂ̃n�[�h�f�B�X�N�Ƀo�b�N�A�b�v�����̂���ԊȒP�Ȏ�i�ł��B�܂��A�e�ʂ��ȒP�ɑ��₷���Ƃ��ł���t�@�C���T�[�o�́A�l�b�g���[�N���o�R�����o�b�N�A�b�v��̑ΏۂƂ��Ă��悭���p����Ă��܂��B
�܂��A�̂���g���Ă���e�[�v�͌��݂ł��o�b�N�A�b�v���f�B�A�Ƃ��Ă悭���p����Ă��܂��B
���ɂ��A�o�b�N�A�b�v�Ώۂ̗e�ʂ������Ȃ��ꍇ�ɂ�CD��DVD���o�b�N�A�b�v���f�B�A�̌��ƂȂ�܂��B�������A�}�̂̎�������r�I�Z�����߁A�����ۑ�����ꍇ�ɂ͕ۊǏꏊ�Ȃǂɒ��ӂ��K�v�ł��B

### ��\�I�ȃo�b�N�A�b�v�c�[��
��Ɠ��̉^�p����ł̓o�b�N�A�b�v��p�̏��p�\�t�g�E�F�A�������g���Ă��܂����ALinux�ŕW���ŗ��p�\�ȗl�X�ȃc�[�����g�p����Ă��܂��B�����̒��ł���\�I�Ȉȉ��̃c�[���ɂ��ĉ�����܂��B

* dd�R�}���h
* dump�R�}���h
* tar�R�}���h
* rsync�R�}���h

### dd�R�}���h
�f�B�X�N�S�̂̃C���[�W���o�͂���c�[���ł��Bdd�R�}���h��p���ăo�b�N�A�b�v���s�����Ƃɂ��A�f�B�X�N�̒��g�����S�ɃR�s�[���邱�Ƃ��ł��܂��B

#### dd�R�}���h�̒���
* �f�B�X�N�̒��g���ۂ��ƃR�s�[�ł��邽�߁AMBR(Master Boot Record)���o�b�N�A�b�v�ł��܂��B
* i�m�[�h�ԍ��Aatime�Actime�Ȃǂ̑������o�b�N�A�b�v�ł��܂��B
* �f�B�X�N����f�B�X�N�ɒ��ڃo�b�N�A�b�v���s���ꍇ�ɂ́A�t�@�C���V�X�e��������ɒ��ڃR�s�[���s���̂ō����ł��B

#### dd�R�}���h�̒Z��
* �f�B�X�N���ۂ��ƃR�s�[���邽�߁A���X�g�A���Ƀt�@�C���V�X�e���̃T�C�Y��p�����[�^��ύX�ł��܂���B�܂��A�t�@�C���V�X�e���Ƀt���O�����g�i�f�Љ��j������ꍇ�ɂ��A���̂܂܃R�s�[����܂��B
* �o�b�N�A�b�v�̍ۂɂ́A�t�@�C���ύX������邽�߃A���}�E���g����K�v������܂��B

### dump�R�}���h
�Â����炠��o�b�N�A�b�v��p�R�}���h�B�t�@�C���V�X�e���P�ʂł̃o�b�N�A�b�v���s���܂��B

#### dump�R�}���h�̒���
* �t�@�C���V�X�e���P�ʂŃo�b�N�A�b�v���邽�߁A�����悭�o�b�N�A�b�v���ł��܂��B
* �����^�����o�b�N�A�b�v���ȒP�ɂł��܂��B
* �e�[�v�ւ̃o�b�N�A�b�v���ł��܂��B
* i�m�[�h�ԍ��Aatime�Actime�Ȃǂ̑������o�b�N�A�b�v�ł��܂��B
* ���X�g�A���Ƀt�@�C���V�X�e���̃T�C�Y��p�����[�^��ύX�ł��܂��B
* �V�����t�@�C���V�X�e���Ƀ��X�g�A����΁A�t���O�����g�������ł��܂��B

#### dump�R�}���h�̒Z��
* �f�B���N�g���P�ʂ�t�@�C���P�ʂł̃o�b�N�A�b�v�͂ł��܂���B
* �o�b�N�A�b�v�t�@�C��������ƁA�ꕔ�̃t�@�C���������~�ςł��܂���B
* ���x�͂��܂葬������܂���B
* ext2/3/4�ł����g�p�ł��܂���B����ȊO�̃t�@�C���V�X�e���̏ꍇ�A���Ƃ���XFS�ɂ�xfsdump�Ȃǐ�p�̃R�}���h���g�p����K�v������܂��B

### tar�R�}���h
�uTape Archiver�v�̖��O�̒ʂ�A���X�̓e�[�v�ւ̃A�[�J�C�u���쐬���邽�߂̃R�}���h�ł����A�t�@�C���Ƃ��ăA�[�J�C�u���쐬���邱�Ƃ��ł��A�_�������܂��B

#### tar�R�}���h�̒���
* �t�@�C���P�ʂ̃o�b�N�A�b�v�A���X�g�A���ł��܂��B
* �����o�b�N�A�b�v���ł��܂��B
* �e�[�v�ւ̃o�b�N�A�b�v���ł��܂��B
* �o�b�N�A�b�v�f�[�^�������Ă��Ă��A�����I�ɕ����ł��܂��B

#### tar�R�}���h�̒Z��
* ���x�͂��܂葬������܂���B
* ���X�g�A����i�m�[�h�ԍ����ς�邽�߁Ai�m�[�h�𒼐ڎQ�Ƃ��Ă���v���O�����ł̓��X�g�A�����t�@�C�������̃t�@�C���Ɠ������ƔF���ł��܂���B

### rsync�R�}���h
�uremote sync�v�̖��O�̒ʂ�A�����[�g�Ńt�@�C����f�B���N�g���𓯊����邽�߂ɍ��ꂽ�R�}���h�ł����A�o�b�N�A�b�v�ɂ��g�p�ł��܂��B�o�b�N�A�b�v��Ƃ��ă��[�J���z�X�g���w�肷�邱�Ƃ��ł��邽�߁A���[�J���Ƀ}�E���g���ꂽ�O���X�g���[�W�Ƀo�b�N�A�b�v���邱�Ƃ��ł��܂��B

#### rsync�R�}���h�̒���
* �t�@�C���P�ʂ̃o�b�N�A�b�v�A���X�g�A���ł��܂��B
* tar�R�}���h���������悭�o�b�N�A�b�v�ł��܂��B
* �����^�����o�b�N�A�b�v���ł��܂��B

#### rsync�R�}���h�̒Z��
* �f�B�X�N���܂邲�ƃo�b�N�A�b�v����ꍇ�ɂ́Add��dump�Ɣ�ׂĒx���ł��B
* ���X�g�A����i�m�[�h�ԍ����ς�邽�߁Ai�m�[�h�𒼐ڎQ�Ƃ��Ă���v���O�����ł̓��X�g�A�����t�@�C�������̃t�@�C���Ɠ������ƔF���ł��܂���B

### �o�b�N�A�b�v�ƃ��X�g�A�̏���
�e�R�}���h���g�p�����o�b�N�A�b�v�ƃ��X�g�A�̕��@���A���ۂɃR�}���h�𓮂����Ȃ��������܂��B

�o�b�N�A�b�v�Ώۂ�/mnt/backup_test�i/dev/sdb1�j�A���X�g�A���/mnt/restore_test�i/dev/sdc1�j�Ƃ��܂��B

���z�}�V���ɉ��z�n�[�h�f�B�X�N��2�A�����T�C�Y�Œǉ����܂��B�ǉ��������z�n�[�h�f�B�X�N��/dev/sdb��/dev/sdc�Ƃ���OS����F���ł���悤�ɁA���z�}�V�����ċN�����܂��B

�����}�V�����g�p���Ă���ꍇ�ɂ́A�����n�[�h�f�B�X�N��2��ǉ����邩�A1��̒ǉ������n�[�h�f�B�X�N��2�̃p�[�e�B�V�����i/dev/sdb1��/dev/sdb2�j���쐬���Ă��������B

�����ALVM�̎��K�Ŏg�p�����n�[�h�f�B�X�N/dev/sdb�����̂܂ܗ��p����ꍇ�ɂ́A�A���}�E���g������fdisk�R�}���h���Ńp�[�e�B�V��������x�폜���Ď��K���s���܂��B

fdisk�R�}���h�Ȃǂ�/dev/sdb�Ƀp�[�e�B�V����/dev/sdb1���쐬���Amkfs.ext4�R�}���h��ext4�t�@�C���V�X�e���ŏ�����������A/mnt/backup_test�Ƀ}�E���g���܂��B��̓I�ȃp�[�e�B�V�����쐬�菇�́ALVM�̎��K���Q�Ƃ��Ă��������B�������A���̎��K�ł�LVM�͎g�p���Ȃ��̂ŁA�p�[�e�B�V�����^�C�v�̕ύX�͕s�v�ł��B

```shell-session
# fdisk /dev/sdb
���p�[�e�B�V�������쐬
# mkfs.ext4 /dev/sdb1 
# mkdir /mnt/backup_test
# mount -t ext4 /dev/sdb1 /mnt/backup_test/
```

/mnt/backup_test�f�B���N�g���ɁA�e�X�g�p�̃f�B���N�g���ƃt�@�C�����쐬���Ă����܂��B

```shell-session
# mkdir /mnt/backup_test/test_dir
# touch /mnt/backup_test/test_dir/test_file
```

### dd�R�}���h���g�����o�b�N�A�b�v
dd�R�}���h�ł̓t�@�C���P�ʂŃo�b�N�A�b�v���ł��Ȃ����߁A/dev/sdb�f�o�C�X���̂��o�b�N�A�b�v���܂��B

/dev/sdc�͏��������Ă��Ȃ���ԂŁAdd�R�}���h�����s���܂��B/dev/sdb���ۂ���/dev/sdc�Ƀo�b�N�A�b�v����܂��B

```shell-session
#  dd if=/dev/sdb of=/dev/sdc
208896+0 records in
208896+0 records out
106954752 bytes (107 MB) copied, 1.29132 s, 82.8 MB/s
```

fdisk�R�}���h���g���āA/dev/sdc1���쐬����Ă��邱�Ƃ��p�[�e�B�V�������Ŋm�F���܂��B/dev/sdc�ɏ������܂ꂽ�p�[�e�B�V��������OS�ɔF�������邽�߂�OS�̍ċN�����s���Ă���A�m�F���܂��B

```shell-session
# reboot
���V�X�e���ċN����Ɋm�F
# fdisk /dev/sdc
�i���j
�R�}���h (m �Ńw���v): ��p ���p�[�e�B�V�������\����p�����

�f�B�X�N /dev/sdc: 106 MB, 106954752 �o�C�g
�w�b�h 255, �Z�N�^ 63, �V�����_ 13
Units = �V�����_�� of 16065 * 512 = 8225280 �o�C�g
�Z�N�^�T�C�Y (�_�� / ����): 512 �o�C�g / 4096 �o�C�g
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
�f�B�X�N���ʎq: 0x43b56949

�f�o�C�X �u�[�g      �n�_        �I�_     �u���b�N   Id  �V�X�e��
/dev/sdc1               1          13      104391   83  Linux
Partition 1 does not start on physical sector boundary.

�R�}���h (m �Ńw���v): ��q ���I����q�����
```

/dev/sdc1��/mnt/restore_test�Ƃ��ă}�E���g���܂��B��ق�/mnt/backup_test�f�B���N�g���ȉ��ɍ쐬�����e�X�g�p�̃f�B���N�g������уt�@�C�������X�g�A����Ă���̂��m�F�ł��܂��B

```shell-session
# mount /dev/sdc1 /mnt/restore_test
# cd /mnt/restore_test
# ls -l
���v 14
drwx------. 2 root root 12288 12�� 22 13:16 2014 lost+found
drwxr-xr-x. 3 root root  1024 12�� 22 13:16 2014 test_dir
[root@server restore_test]# ls -l test_dir/
���v 0
-rw-r--r--. 1 root root 0  12�� 22 13:16 2014 test_file
```

### dump�R�}���h�ɂ��o�b�N�A�b�v
dump�R�}���h�ɂ��o�b�N�A�b�v�̓t�@�C���V�X�e���P�ʂōs���܂��B�o�b�N�A�b�v�Ώۂ̑I���́A�ݒ�t�@�C��/etc/fstab�ōs���܂��B

�����ł͗�Ƃ���/boot�f�B���N�g���S�̂��t�@�C���Ƃ��ăo�b�N�A�b�v���܂��B/boot�f�B���N�g���́A/�i���[�g�j�f�B���N�g���Ƃ͕ʂ̃p�[�e�B�V�����Ƀt�@�C���V�X�e���������/boot�f�B���N�g���Ƀ}�E���g����Ă���̂ŁA/boot�f�B���N�g���ȉ������ׂ�dump�R�}���h�Ńo�b�N�A�b�v�ł��܂��B

CentOS 6�ł�dump�R�}���h���W���ŃC���X�g�[������Ă��Ȃ����߁Adump�p�b�P�[�W���C���X�g�[�����܂��B

```shell-session
# yum install dump
```

dump�R�}���h�ɂ��o�b�N�A�b�v�Ώۂ�/etc/fstab�ɐݒ肵�܂��B/etc/fstab��5�Ԗڂ̃t�B�[���h�i�ォ��2�Ԗځj���u1�v�ɐݒ肳��Ă���t�@�C���V�X�e����dump�R�}���h�̑ΏۂƂȂ�܂��B/boot�f�B���N�g���Ƀ}�E���g�����t�@�C���V�X�e����dump�R�}���h�̑ΏۂɂȂ��Ă��邱�Ƃ��m�F���܂��B/proc��/sys�Ȃǂ̋[���t�@�C���V�X�e���͑ΏۊO�ƂȂ�܂��B

```shell-session
# vi /etc/fstab

/dev/mapper/vg_cent65-lv_root /                       ext4    defaults
1 1
UUID=fe4d3f56-a570-44b4-a863-418b789b42bc /boot                   ext4
defaults        ��1�� 2
/dev/mapper/vg_cent65-lv_swap swap                    swap    defaults
0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
```

dump�R�}���h�����s���āA/boot�f�B���N�g�����o�b�N�A�b�v���܂��B�ʏ�̓e�[�v�Ȃǂ̃o�b�N�A�b�v���f�B�A�ɑ΂��ăo�b�N�A�b�v���s���܂����Adump�R�}���h�̏o�͂��p�C�v��dd�R�}���h�ɓn�����ƂŃt�@�C���Ƃ��ăo�b�N�A�b�v�ł��܂��B
�t�^���Ă���I�v�V�����̈Ӗ��͈ȉ��̒ʂ�ł��B��ł́A�o�͐�ɕW���o�͂ł���u-�v�i�n�C�t���j���w�肵�Ă���_�ɒ��ӂ��Ă��������B

|�I�v�V����|�Ӗ�|
|-------|-------|
|-0|���x��0�̃o�b�N�A�b�v���擾����B���x��0�̓t���o�b�N�A�b�v|
|-u|�o�b�N�A�b�v������A/etc/dumpdates���X�V�B�����o�b�N�A�b�v�ɕK�v|
|-a|�����T�C�Y�B�o�b�N�A�b�v���f�B�A����I���ʒm������܂ŏ�������|
|-n|operator�O���[�v�ɑ΂��Ēʒm���s��|
|-f|�o�͐���w��|

```shell-session
# dump -0uan -f - /boot | dd of=/tmp/boot.dump
  DUMP: No group entry for operator.
  DUMP: Date of this level 0 dump: Thu Jan 15 00:07:19 2015
  DUMP: Dumping /dev/sda1 (/boot) to standard output
�i���j
  DUMP: Date this dump completed:  Thu Jan 15 00:07:20 2015
  DUMP: Average transfer rate: 26570 kB/s
  DUMP: DUMP IS DONE
53140+0 records in
53140+0 records out
27207680 bytes (27 MB) copied, 0.202273 s, 135 MB/s

# ls -l /tmp/boot.dump 
-rw-r--r--. 1 root root 27207680  1�� 15 00:07 2015 /tmp/boot.dump
```

restore�R�}���h�����s���āA/tmp/restore_test�f�B���N�g���Ƀ��X�g�A���܂��B-r�I�v�V�����́A�t�@�C���V�X�e�������ׂă��X�g�A���邱�Ƃ��w�肵�Ă��܂��B-f�I�v�V�����́A���͂Ƃ��ĕW�����͂ł���u-�v�i�n�C�t���j���w�肵�Ă��܂��Bdump�R�}���h�ō쐬�����o�b�N�A�b�v�t�@�C����cat�R�}���h�œǂݍ��݁A�W���o�͂��p�C�v��restore�R�}���h�̕W�����͂ɓn���Ă��܂��B

```shell-session
# mkdir /tmp/restore_test
# cd /tmp/restore_test
# cat /tmp/boot.dump | restore -rf -
# ls
System.map-2.6.32-504.el6.x86_64  initramfs-2.6.32-504.el6.x86_64.img
config-2.6.32-504.el6.x86_64      lost+found
efi                               symvers-2.6.32-504.el6.x86_64.gz
grub                              vmlinuz-2.6.32-504.el6.x86_64
```

/tmp/restore_test�f�B���N�g�����̃t�@�C�������ׂč폜���܂��B

```shell-session
# rm -rf /tmp/restore_test/*
```

### tar�R�}���h�ɂ��o�b�N�A�b�v
tar�R�}���h�̓t�@�C���A�f�B���N�g�����A�[�J�C�u�Ƃ��ĂЂƂ܂Ƃ߂ɂ��ăo�b�N�A�b�v���s���܂��B�o�b�N�A�b�v��ړI�Ƃ����g�p�̂ق��A���Ƃ���Linux�J�[�l���̃\�[�X�R�[�h�Ȃǂ���ɂ܂Ƃ߂Ĕz�z����ړI�ł��g�p����Ă��܂��B

/boot�f�B���N�g���ȉ��̃t�@�C������уf�B���N�g�����o�b�N�A�b�v���܂��B�A�[�J�C�u�t�@�C����/tmp/boot_backup.tar�Ƃ��܂��B�A�[�J�C�u�̍쐬�́Atar�R�}���h��-c�I�v�V������t�^���Ď��s���܂��B

```shell-session
# tar -cvf /tmp/boot_backup.tar /boot
tar: �����o������擪�� `/' ����菜���܂�
/boot/
/boot/grub/
�i���j
/boot/System.map-2.6.32-504.el6.x86_64
/boot/.vmlinuz-2.6.32-504.el6.x86_64.hmac

# ls -l /tmp/boot_backup.tar
-rw-r--r--. 1 root root 26982400  1�� 15 00:15 2015 /tmp/boot_backup.tar
```

/tmp/restore_test�f�B���N�g���Ƀt�@�C�������X�g�A���܂��B�A�[�J�C�u����̃t�@�C���̎��o���́Atar�R�}���h��-x�I�v�V������t�^���Ď��s���܂��B�t�@�C���̓J�����g�f�B���N�g���ȉ��ɓW�J����܂��B

```shell-session
# cd /tmp/restore_test
# tar -xvf /tmp/boot_backup.tar
boot/
boot/grub/
�i���j
boot/System.map-2.6.32-504.el6.x86_64
boot/.vmlinuz-2.6.32-504.el6.x86_64.hmac
# ls -l
���v 4
dr-xr-xr-x. 5 root root 4096  1��  6 06:20 2015 boot
# ls boot/
System.map-2.6.32-504.el6.x86_64  initramfs-2.6.32-504.el6.x86_64.img
config-2.6.32-504.el6.x86_64      lost+found
efi                               symvers-2.6.32-504.el6.x86_64.gz
grub                              vmlinuz-2.6.32-504.el6.x86_64
```

/tmp/restore_test�f�B���N�g�����̃t�@�C�����폜���܂��B

```shell-session
# rm -rf /tmp/restore_test/*
```

### rsync�R�}���h�ɂ��o�b�N�A�b�v
rsync�R�}���h�́A�t�@�C���A�f�B���N�g�����o�b�N�A�b�v���邱�Ƃ��ł��܂��B�l�b�g���[�N�o�R�ŕʂ̃z�X�g�փo�b�N�A�b�v���s���Ȃǂ̗p�r�Ɏg�p���܂��B�����Ƃ��āA�V���ɒǉ����ꂽ�t�@�C���̂݃o�b�N�A�b�v���邱�Ƃ��ł��܂��B

�ȉ��̗�ł́A����z�X�g����/boot�f�B���N�g�����̃t�@�C����ʂ̃f�B���N�g���Ƀo�b�N�A�b�v���Ă��܂��B

rsync�R�}���h�����s���āA/boot�f�B���N�g����/tmp/restore_test�f�B���N�g���ȉ��Ƀo�b�N�A�b�v���܂��B

```shell-session
# rsync -av /boot /tmp/restore_test
sending incremental file list
boot/
boot/.vmlinuz-2.6.32-504.el6.x86_64.hmac
�i���j
boot/grub/xfs_stage1_5
boot/lost+found/

sent 26964672 bytes  received 457 bytes  53930258.00 bytes/sec
total size is 26959690  speedup is 1.00
```

/tmp/restore_test�f�B���N�g���ȉ��̃t�@�C�����m�F���܂��B

```shell-session
# ls -l /tmp/restore_test
���v 4
dr-xr-xr-x. 5 root root 4096  1��  6 06:20 2015 boot
# ls -l /tmp/restore_test/boot
���v 25848
-rw-r--r--. 1 root root  2544748 10�� 15 13:54 2014 System.map-2.6.32-504.el6.x86_64
-rw-r--r--. 1 root root   106308 10�� 15 13:54 2014 config-2.6.32-504.el6.x86_64
�i���j
-rw-r--r--. 1 root root   200191 10�� 15 13:55 2014 symvers-2.6.32-504.el6.x86_64.gz
-rwxr-xr-x. 1 root root  4152336 10�� 15 13:54 2014 vmlinuz-2.6.32-504.el6.x86_64
```

/boot/rsync_test�t�@�C����V�K�ɍ쐬���܂��B

```shell-session
# touch /boot/rsync_test
# ls -l /boot/rsync_test 
-rw-r--r--. 1 root root 0  1�� 15 00:23 2015 /boot/rsync_test
```

�ēxrsync�R�}���h�����s���܂��B�V���ɒǉ����ꂽ�t�@�C���̂݃o�b�N�A�b�v����܂��B

```shell-session
# rsync -av /boot /tmp/restore_test
sending incremental file list
boot/
boot/rsync_test

sent 832 bytes  received 40 bytes  1744.00 bytes/sec
total size is 26959690  speedup is 30917.08
```

�V���Ƀo�b�N�A�b�v���ꂽ�t�@�C�����m�F���܂��B

```shell-session
# ls -l /tmp/restore_test/boot/rsync_test
-rw-r--r--. 1 root root 0  1�� 15 00:23 2015 /tmp/restore_test/boot/rsync_test
```

tmp/restore_test�f�B���N�g�����̃t�@�C�����폜���܂��B

```shell-session
# rm -rf /tmp/restore_test/*
```

