---
description: 면불 API
---

# Myeonbul

| Code | Explanation |
| :--- | :--- |
| 401 Unauthorized | 유효하지 않은 JWT |
| 500 Internal Server Error | 서버 오류 |

### 정보

* 면불 ID : 날짜\(YYYYMMDD\)\_ID
* 면불 장소 : 문자열
* 면불 일자 : 연도 4자리 + 월 2자리 + 일 2자리
* 면불 시작 시간 : 시 2자리 + 분 2자리
* 면불 종료 시간 : 시 2자리 + 분 2자리
* 면불 담당 선생님 : 문자열
* 면불 해당 학생 : 문자열 리스트
* 면불 사유 : 문자열

**보안상의 이유로 HTTPS 연결에서만 Myeonbul API가 작동합니다.**

{% api-method method="post" host="https://api.iasa.kr" path="/myeonbul" %}
{% api-method-summary %}
면학 불참 생성
{% endapi-method-summary %}

{% api-method-description %}
jwt 토큰에 따라 학생이면 verify=false, 선생님이면 verify=true
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=true %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="title" type="string" required=true %}
면불 사유
{% endapi-method-parameter %}

{% api-method-parameter name="students" type="array" required=true %}
학번, 정수 리스트로 제공
{% endapi-method-parameter %}

{% api-method-parameter name="teacher" type="integer" required=true %}
선생님 일련번호
{% endapi-method-parameter %}

{% api-method-parameter name="end\_time" type="integer" required=true %}
면불 종료시간, 4자리 정수\(ex:2100\)
{% endapi-method-parameter %}

{% api-method-parameter name="start\_time" type="integer" required=true %}
면불 시작시간, 4자리 정수\(ex:1900\)
{% endapi-method-parameter %}

{% api-method-parameter name="date" type="integer" required=true %}
날짜, 8자리 정수 \(ex:20191122\)
{% endapi-method-parameter %}

{% api-method-parameter name="place" type="string" required=true %}
면불 장소
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
면불 ID 반환
{% endapi-method-response-example-description %}

```
20190906_4
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}
추후 구현 예정
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.iasa.kr" path="/myeonbul" %}
{% api-method-summary %}
면학 불참 수정
{% endapi-method-summary %}

{% api-method-description %}
면불 데이터를 수정합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=true %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
면불 id
{% endapi-method-parameter %}

{% api-method-parameter name="place" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="date" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="start\_time" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="end\_time" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="teacher" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="students" type="array" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="title" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.iasa.kr" path="/myeonbul" %}
{% api-method-summary %}
면학 불참 삭제
{% endapi-method-summary %}

{% api-method-description %}
면불 ID를 받아 데이터베이스에서 삭제합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
 면불 ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=true %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.iasa.kr" path="/myeonbul/verify" %}
{% api-method-summary %}
 면학 불참 승인
{% endapi-method-summary %}

{% api-method-description %}
면불을 승인합니다.  
jwt 토큰 확인후 선생님인 경우만 처리하고 학생인 경우는 http 403 코드를 리턴합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
면불 ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=true %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Myeonbul has been verified.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=403 %}
{% api-method-response-example-description %}
Your account does not have the necessary permissions to authorize Myeonbul record.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
There is no Myeonbul entry for the ID.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.iasa.kr" path="/myeonbul/verify" %}
{% api-method-summary %}
면학 불참 승인상태 확인
{% endapi-method-summary %}

{% api-method-description %}
면불이 선생님에 의해 승인되었는지 확인합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
면불 ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=true %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Myeonbul is authorized
{% endapi-method-response-example-description %}

```
{ 
   "status":"Not verified"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=202 %}
{% api-method-response-example-description %}
Myeonbul is not authorized yet.
{% endapi-method-response-example-description %}

```
{ 
   "status":"Not verified"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.iasa.kr" path="/myeonbul/" %}
{% api-method-summary %}
학생 면불 목록 조회
{% endapi-method-summary %}

{% api-method-description %}
특정 학번의 면불 목록을 조회합니다.  
**추후 구현 예정**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="student" type="integer" required=true %}
조회할 학생의 학번
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=true %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
면불 ID로 이루어진 배열을 반환합니다.
{% endapi-method-response-example-description %}

```
{ 
   "data":[ 
      "20191121_1",
      "20191122_5",
      "20191122_6"
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.iasa.kr" path="/myeonbul/info" %}
{% api-method-summary %}
면불 정보 조회
{% endapi-method-summary %}

{% api-method-description %}
면불 ID를 제공 시 면불에 대한 정보를 제공합니다.  
**추후 구현 예정**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=false %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
면불 id
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
   "title":"융복합 준비",
   "students":[ 
      "20190001",
      "20190002"
   ],
   "teacher":1,
   "start_time":1920,
   "end_time":2330,
   "date":20191122,
   "place":"컴퓨터실 I"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="head" host="https://api.iasa.kr" path="/myeonbul" %}
{% api-method-summary %}
  면불 여부 조
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="barcode" type="integer" required=false %}
 바코드 번호 
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
 현재 시각 면불 대상임 
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
현재 시각 면불 대상이 아
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
 바코드를 찾을 수 없거나 서버 처리 중 에러.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

