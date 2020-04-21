---
description: 급식 API
---

# 급식

{% api-method method="get" host="https://api.iasa.kr" path="/meal" %}
{% api-method-summary %}
 급식 정보 
{% endapi-method-summary %}

{% api-method-description %}
급식 데이터를 가져옵니다.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="date" type="integer" required=false %}
정보를 가져올 날자를 나타내는 8자리 숫자
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="integer" %}
가져올 급식의 종류. 0:아침, 1:점심, 2:
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{    "name": "Cake's name",    "recipe": "Cake's recipe name",    "cake": "Binary cake"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```
{    "message": "Ain't no cake like that."}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



