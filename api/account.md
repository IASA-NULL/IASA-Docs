---
description: 계정 API
---

# Account

모든 계정 API는 https 프로토콜에서만 작동합니다.

{% api-method method="post" host="https://api.iasa.kr" path="/account/signin" %}
{% api-method-summary %}
로그인
{% endapi-method-summary %}

{% api-method-description %}
추후 구현 예정
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
비밀번호
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
이메일
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
로그인 성공, jwt 반환
{% endapi-method-response-example-description %}

```
{"jwt":"12345"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
로그인 실패
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.iasa.kr" path="/account/signup" %}
{% api-method-summary %}
회원가입
{% endapi-method-summary %}

{% api-method-description %}
사용자 이메일로 인증 메일을 전송합니다.  
밑의 이메일 인증에서 사용할 id\(uuid기반\) 생성/저장합니다.  
이메일 인증시 next 파라미터는 https://iasa.kr/signup/finalize입니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="studentId" type="string" required=false %}
학번
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
비밀번호
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
이메일
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
성공
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
오류
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.iasa.kr" path="/account/verify/" %}
{% api-method-summary %}
이메일 인증
{% endapi-method-summary %}

{% api-method-description %}
이메일 인증에 첨부되는 링크입니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="next" type="string" required=true %}
이동할 페이지, base64로 인코딩됨
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
요청 일련번호
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}
인증 성공시 요청 페이지로 리다이렉션  
인증 실패시 https://iasa.kr/signup/fail로 이
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.iasa.kr" path="/account/studentid" %}
{% api-method-summary %}
학번 불러오기
{% endapi-method-summary %}

{% api-method-description %}
jwt 토큰을 받으면 학번을 리턴합니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="auth" type="string" required=false %}
jwt 토큰
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
학번
{% endapi-method-response-example-description %}

```
{'studentId':2019001}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

