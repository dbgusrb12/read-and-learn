# HTTP 리퀘스트 메시지를 작성한다.

## 탐험 여행은 URL 입력부터 시작한다.

### URL (Uniform Resource Locator) 이란?

`http:`, `ftp:`, `file:`, `mailto:` 등으로 시작하는 문자열로,  
웹에 존재하는 수많은 자원들을 식별할 때 사용하는 식별자이며, 주소체계이다.   

맨 앞에 있는 문자열로 액세스하는 방법을 표현하며, 그 뒤에 오는 문자열은 액세스 대상에 따라 형식이 다르다.

### URL 의 형식

HTTP 프로토콜로 웹 서버에 액세스 하는 경우

- `http://사용자명(생략가능):패스워드(생략가능)@웹 서버의 도메인명:포트번호(생략가능)/파일의 경로명`
- ex) <http://user:password@www.hyungyu.co.kr:80/dir/file1.html>

FTP 프로토콜로 파일 다운로드/업로드 하는 경우

- `ftp://사용자명(생략가능):패스워드(생략가능)@FTP 서버의 도메인명:포트번호(생략가능)/파일의 경로명`
- ex) <ftp://user:password@ftp.hyungyu.co.kr:21/dir/file1.html>

클라이언트 PC 자체의 파일에서 데이터를 읽어오는 경우

- `file://컴퓨터명(생략가능)/파일의 경로명`
- ex) <file://localhost/c:/dir/file1.jpg>

메일을 송신하는 경우

- `mailto:메일주소`
- ex) <mailto:hyungyu@hyungyu.co.kr>

뉴스그룹의 기사를 읽는 경우

- `news:뉴스그룹명`
- ex) <news:sample.protocols.tcp-ip>

## 브라우저는 먼저 URL을 해독한다.

브라우저는 웹 서버에 보내는 리쿼스트의 메시지를 작성하기 위해 URL 을 해독한다.

### URL 의 요소 (HTTP 기준)

http://www.hyungyu.co.kr/dir/file1.html

위의 URL 을 기준으로,   
- `http:` : 데이터 출처에 액세스하는 방법 (프로토콜)
- `//` : 해당 문자 뒤에 오는 문자열이 서버의 이름임을 나타냄
- `www.hyungyu.co.kr` : 웹 서버명
- `/dir/file1.html` : /디렉토리/.../파일명 으로 되어있는 데이터 출처의 경로명

## 파일명을 생략한 경우

위의 나온 URL과 다르게 `/`로 끝나는 URL은 파일명을 생략한 경우로,  
서버측에서 설정한 파일을 액세스한다. (`default.htm`, `index.html`)  

### <http://www.hyungyu.co.kr/dir/>  

파일명만 생략된 경우, `/dir` 디렉토리 내에 기본 설정된 파일 액세스 (`/dir/default.htm`, `/dir/index.html`)

### <http://www.hyungyu.co.kr/>

파일명만 생략된 경우, 루트(`/`) 디렉토리 내에 기본 설정된 파일 액세스 (`/default.htm`, `/index.html`)

### <http://www.hyungyu.co.kr>

디렉토리명도 생략 된 경우, 루트(`/`) 디렉토리 내에 기본 설정된 파일 액세스 (`/default.htm`, `/index.html`)

### <http://www.hyungyu.co.kr/whatisthis>

규칙에 따르면 whatisthis 를 파일명으로 보는게 맞지만, 웹 서버에 해당 이름의 파일이 있으면 파일명으로,  
해당 이름의 디렉토리가 있으면 디렉토리로 취급하는 것이 통례이다. (`/whatisthis`, `/whatisthis/index.html`, `/whatisthis/default.htm`)

같은 이름을 가진 디렉토리와 파일은 존재 할 수 없기 때문에 둘 다 있는 경우는 없다.

## HTTP의 기본 개념

