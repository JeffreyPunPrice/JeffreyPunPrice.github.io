---
title: setupAuthentication (Function)
---

Get token data and cookies from [loginAndGetToken](loginAndGetToken)

## Return

| key       |                                        |
| --------- | -------------------------------------- |
| authToken | access token from tokendata            |
| cookies   | cookies directly from loginAndGetToken |
| memberId  | tokenData.claims.user_id               |
| userName  | userName                               |
