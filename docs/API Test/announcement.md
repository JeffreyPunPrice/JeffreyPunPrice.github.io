---
title: Announcement
---

# prerequisite action

Login through `setupAuthentication`

## Postman setup

JWT is needed. set jwt token to environment

```javascript
// at post-response section of generate token request
var jsonData = pm.response.json();
var jwtToken = jsonData.data[0].access_token;
pm.environment.set('jwt_token', jwtToken);
```

Then use `Bearer Token` in Authorization and take `{{jwt_token}}` from the environment

## Request

| GET | `https://apisuat.price.com.hk/announcement/v1/published/members/${memberId}/announcements` |
| --- | ------------------------------------------------------------------------------------------ |

## Response

| key   |                                             |
| ----- | ------------------------------------------- |
| data  | announcement data                           |
| meta  | data about all announcement like totalItems |
| links | request links for related result            |
