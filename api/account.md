---
description: 계정 API
---

# Account

모든 계정 API는 https 프로토콜에서만 작동합니다.

{% api-method method="post" host="https://api.iasa.kr/" path="account/login" %}
{% api-method-summary %}
로그
{% endapi-method-summary %}

{% api-method-description %}
추후 구현 예
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=false %}
비밀번호
{% endapi-method-parameter %}

{% api-method-parameter name="id" type="string" required=true %}
아이디
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



