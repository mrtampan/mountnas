# Mount Nas

Konfigurasi Mount FTP dari folder NAS ke Server Ubuntu

## Requirement
- NAS synology / NAS lainnya
- Server Ubuntu

## Activate FTP Setup Synology

- Buat User, yg nantinya akan menjadi akses ftp user 
- sediakan 1 shared folder dan berikan ke privilage user tersebut.

Setup FTP: https://www.youtube.com/watch?v=aMd67v_SKmU



## Fuse Configuration
edit file `/etc/fuse.conf` didalam server ubuntu

```
# Set the maximum number of FUSE mounts allowed to non-root users.
# The default is 1000.

mount_max = 1000

# Allow non-root users to specify the 'allow_other' or 'allow_root'
# mount options.

user_allow_other
```

hapus `#` di depannya user_allow_other


## Create Folder di server

commandnya:
mkdir path

contohnya seperti ini: `mkdir /var/mountnas`


## Mounting FTP nya NAS ke server

commandnya:
curlftpfs ftphost path -o user=ftpUser:ftpPass,allow_other

contohnya seperti ini: curlftpfs ftp.mrtampan.id /var/mountnas -o user=mrtampan:mrtampan12345,allow_other

## Unmount FTP

commandnya:
fusermount -u path

contohnya seperti ini: `fusermount -u /var/mountnas`

## Share ke webserver

buat symlink aja jika mau dishare ke web / apache server

https://www.hostinger.co.id/tutorial/symbolic-link-linux


Semoga Mantappp
