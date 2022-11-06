# Application Layer

애플리케이션 계층

HTTP, SMTP, SSH, FTP 가 대표적이며 웹 서비스, 이메일 등 **서비스가 실질적으로 제공되는 계층**

## HTTP

HyperText Transfer Protocol 의 약자로 초기 서버와 브라우저간 데이터를 주고 받기 위해 설계된 프로토콜

현재는 서버와 서버간의 통신시에도 많이 이용

#### Http 특징은 아래와 같다

1. HTTP는 헤더를 통한 확장성이 쉽다 => 요청시 헤더값에 쉽게 추가할 수 있다

2. stateless 하다 => 서버가 상태를 저장하지 않는다

## SSH

Secure SHhell Protocol 의 약자로 보안되지 않은 네트워크에서 네트워크 서비스를 안전하게 운영하기 위한 **암호화 네트워크 프로토콜**

## FTP

File Transfer Protocol 의 약자로 노드와 노드간의 **파일을 전송**하는데 사용되는 프로토콜

현재는 파일을 암호화해서 전송하는 FTPS 또는 SFTP 로 대체 !

## SMTP

Smiple Mail Transfer Protocol 로 인터넷을 통해 **메일을 보낼 때** 사용되는 프로토콜

node.js 를 통해 메일을 보낸다면 이를 통해 보내야한다 !

_JS 의 Nodemailer 라이브러리 존재_

---

# Internet Layer

인터넷 계층

IP , ICMP, ARP 가 대표적이며 한 노드에서 다른 노드로 전송 계층에서 받은 세그먼트 또는 데이터그램을 패킷화 하여 전송한다

## ICMP

ICMP ( Internet Control Message Protocol ) 는 노드와 노드 사이에서 **통신이 잘되나 확인**할 때 쓰는 프로토콜로 데이터를 교환하는데 사용되지는 않는다

독립적인 비연결형 프로토콜 !
