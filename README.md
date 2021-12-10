# AWS 세팅



## 시작전 세팅
```text
- https://mozi.tistory.com/191
    putty 접속

- https://app-developer.tistory.com/92
    ftp 서버 설치
```
## ftp 서버 설치
```
sudo yum -y install vsftpd
```
서버 설치
<br /><br />

```
sudo vi /etc/vsftpd/vsftpd.conf
```
anonymous_enable=YES => anonymous_enable=NO
수정
<br /><br />

```
sudo vi /etc/vsftpd/vsftpd.conf
```
```
##pasv options added
pasv_enable=YES
pasv_min_port=1024
pasv_max_port=1048
pasv_address=xx.xxx.xxx.xxx
```
pasv_address에는 EC2 인스턴스의 public ip 기입
<br /><br />


## ubuntu APM 설치

```bash
sudo apt update 
sudo apt install apache2
sudo apt install mysql-server
sudo apt install php libapache2-mod-php php-mysql
```

## AWS EC2 APM 설치

```bash
sudo yum install -y httpd
sudo amazon-linux-extras enable mariadb10.5
sudo yum install -y mariadb-server mariadb
sudo amazon-linux-extras enable php7.4
sudo yum install -y php-cli php-pdo php-fpm php-json php-mysqlnd
```

## 서비스 실행
```
sudo service httpd start
sudo service mariadb start

```

## apache2.conf

```text
<Directory /var/www/html>
 Options Indexes FollowSymLinks
 AllowOverride all
 Require all granted
</Directory>
```

## Apache rewrite 모듈 활성화

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

## mysql root 유저 비밀번호 설정

```
sudo mysql
grant usage on *.* to 'root'@'localhost' identified by '<YOUR PASSWORD>';
```
