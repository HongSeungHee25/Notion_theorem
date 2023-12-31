# JavaScript 정규표현식
## 휴대폰번호 양식 정규식 검사
`/^\d{3}[-.]\d{3}[-.]\d{4}$/;` <br>
 ┗> 전화번호 형식은 xxx-xxxx-xxxx 또는 xxx.xxxx.xxx 형식이여야 합니다.

## 이메일 양식 정규식 검사
`/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;`<br>
┗> 1. 로컬 파트 (Local Part): 소문자(a-z), 대문자(A-Z), 숫자(0-9), 특수문자('_','%','+','-','.')로 구성된 문자열이어야 합니다.<br>
┗> 2. '@' 기호가 있어야 합니다.<br>
┗> 3. 도메인 파트 (Domain Part): 소문자(a-z), 대문자(A-Z), 숫자(0-9), 특수문자('-','.')로 구성된 문자열이어야 하며, 적어도 하나의 '.'이 포함되어야 합니다.<br>
┗> 4. 최소한 두 개의 문자로 이루어진 최상위 도메인 (예: .com, .org, .net 등)이어야 합니다.<br>

## ID 양식 정규식 검사
`/^[a-zA-Z0-9]{5,}$/;`<br>
┗> 최소 5자 이상, 영문자와 숫자만 허용 <br>

## 패스워드 양식 정규식 검사
`/^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[!@#$%^&*()_+\-=[\]{}|;':",./<>?]).{8,}$/;`<br>
┗> 최소 8자 이상, 최소 하나의 숫자, 대문자, 소문자 포함, 특수문자 허용<br>

## 숫자만 포함하는지 확인하는 정규식 검사
`/^\d+$/;`<br>

## 영문자만 포함하는지 확인하는 정규식 검사
`/^[A-Za-z]+$/;`<br>

## 이메일 주소에서 도메인 파트 추출하는 정규식 검사
`/@(.+)/;` <br>

## 이메일 주소에서 로컬 파트와 도메인 파트 추출하는 정규식 검사
`/^([a-zA-Z0-9._%+-]+)@([a-zA-Z0-9.-]+)\.([a-zA-Z]{2,})$/;`<br>

## URL 에서 도메인 추출하는 정규식 검사
`/^https?:\/\/(www\.)?([^\/]+)/;`<br>

## 날짜 형식(yyyy-mm-dd) 확인하는 정규식 검사
`/^\d{4}-(0\d|1[0-2])-(0\d|1\d|2\d|3[0-1])$/;`<br>

## 주민등록번호 형식 확인하는 정규식 검사
`/^\d{6}-?\d{7}$/;`<br>

## 유효한 전화번호 포맷으로 변환하는 정규식 검사
`/(\d{3})(\d{4})(\d{4})/;`<br>

## 유효한 IPv4 주소 추출하는 정규식 검사
`/\b(?:\d{1,3}\.){3}\d{1,3}\b/g;`<br>
┗> 추출 전 = 'IP addresses: 192.168.0.1, 10.0.0.1, and 255.255.255.0'; -> 추출 후 = ['192.168.0.1', '10.0.0.1', '255.255.255.0']

