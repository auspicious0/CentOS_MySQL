# MySQL 설치 가이드

이 문서는 MySQL Community Edition을 Red Hat Enterprise Linux 7 또는 Oracle Linux 7에 설치하는 과정을 안내합니다.

## 1. MySQL Community Edition 다운로드

- [MySQL 공식 웹사이트](https://www.mysql.com/products/community/)에서 다운로드 가능합니다.
- MySQL Yum Repository 페이지로 이동합니다.
- Red Hat Enterprise Linux 7 또는 Oracle Linux 7에 맞는 버전을 선택합니다.

## 2. MySQL Repository 설치

```bash
sudo yum install -y https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
yum repolist enabled | grep "mysql.*"  # 설치 확인
yum search mysql  # 패키지 목록 확인
```


## 3. MySQL 설치

```bash
yum install -y mysql-server
mysqld –V #버전확인 필수 – mariaDB로 설치될 가능성이 농후
```

## 4. MySQL 서버 시작 및 비밀번호 변경

```bash
systemctl enable mysqld && systemctl start mysqld && systemctl status mysqld (서버시작)
grep 'temporary password' /var/log/mysqld.log(서버에 접속하기 위한 임시 비밀번호 확인)
mysql -u root –p (서버 접속)
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY ‘본인이 원하는 비밀번호'; (비밀번호 변경)
```
 
https://1mini2.tistory.com/86 
사이트를 참조
