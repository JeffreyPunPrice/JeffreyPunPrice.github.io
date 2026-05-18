---
title: loginAndGetToken (Function)
---

# Login

| Method | URL                                  |
| ------ | ------------------------------------ |
| POST   | `https://uat.price.com.hk/login.php` |

| Header          | value                                                                                   |
| --------------- | --------------------------------------------------------------------------------------- |
| Accept          | text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,\*/\*;q=0.8 |
| Accept-Language | en-US,en;q=0.5                                                                          |
| Content-Type    | application/x-www-form-urlencoded                                                       |
| User-Agent      | Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/115.0    |
| Connection      | keep-alive                                                                              |

| form-data   | value                                                         |
| ----------- | ------------------------------------------------------------- |
| member_type | p                                                             |
| referer     | `https://uat.price.com.hk/index.php?login_auto_jump=0&popup=` |
| username    | nightly00 (e.g.)                                              |
| password    | Abcd1234 (e.g.)                                               |
| auto_login  | 1                                                             |

## Response

| Cookie          |
| --------------- |
| AB_42           |
| AB_60           |
| AB_full         |
| nwtc            |
| dfp_seg_ids     |
| price_ui_cookie |

In `authentoication.ts`
Extract cookie only `nwtc` `ui_site` `ui_uname` `ui_uid` `price_ui_cookie` `ui_authcode` `ui_auth_hash`

# GenerateToken

| Method | URL                                                                            |
| ------ | ------------------------------------------------------------------------------ |
| POST   | `https://apisuat.price.com.hk/authentication/v1/published/member/token/legacy` |


| Header       |                                                            |
| ------------ | ---------------------------------------------------------- |
| Cookie       | _Extracted cookie with nwtc, ui_site,ui_uname, ui_uid ..._ |
| Accept       | _/_                                                        |
| Content-Type | application/json                                           |

Body (raw)

```
{
    "device_description": "Automation Positive",
    "use_cookie": true
}
```

## Response (example)

```
{
    "data": [
        {
            "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJtZW1iZXIvMjM5NjgyMCIsInVzZXJJZCI6IjIzOTY4MjAiLCJ1c2VybmFtZSI6Im5pZ2h0bHkwMCIsInVzZXJUeXBlIjoibWVtYmVyIiwic2NvcGUiOiJVOioiLCJqdGkiOiI2YTA1NGUwYWE5MTA2OGNlZDFhMTFjNGIiLCJpYXQiOjE3Nzg3MzI1NTQsImV4cCI6MTc3ODczMzE1NH0.eeCAvbky6FIZpHteaMMw5ne7jseuBRv299BBQ-Sc8yopjZoT6cFeT0vu9a5GXzzT4V1ae1NhpvC76-K5-Sb_TSQ3Lj37agN2IL_wjnCXIQnVJBAnLlttfTc0Sa42EQyY6w1TgJeImRduue9yNc6V8qjkwT03XVZbu3hTrRO4j4MWl1NDSucVoSubnqsTxy88A7Cafguxrll81oDyKPGh_f96xOVHUvoajrsYZG8avJ7ZWKPJISudRfM3HgSUoMDUNhAbF-CtMNKJSur-_9GnbM-6rU4SeRySkREqvjJ-Jc4YF7WuhK1WRZcPOd5KaYa6wI19zafL97tiWc7MbKZ2PXV677qbyVGtzn7z9jhsQxzF6QlcaIl0wJTXJNO1vh-A5KzeblfrfjzzJOfhFYeuEUZMjw6MS6oEpSPqsZoVttkZD6c48MFr29ddSE05QimLMb49TDCiYUVsm2cJLvDPpaALG4OGShaFmIN6G-i8MdUZ-A2XyA-bU2FaxOXoVRLEd_EQikkIdZ7J8ydJmeNcej1_ZGpE86ql7L1NZttZMk-kHSiII8C_rACbXQvh9get0dZNatiU8KtruqHF_0GoRIPQyvFuNLAYoa2tOnYMsnNjZ-N6so2Nium32ZERSwdeIOvB2cIQeOi5OwAvwmjiJmb7aXAbdej-4N613YMrucU",
            "expires_in": 600,
            "id": "6a054e0aa91068ced1a11c4b",
            "claims": {
                "user_id": "2396820",
                "user_type": "member",
                "username": "nightly00",
                "scope": "U:*"
            },
            "token_type": "bearer"
        }
    ]
}
```

## Return

| key       |                                                            |
| --------- | ---------------------------------------------------------- |
| tokenData | data from response#2                                       |
| cookies   | _Extracted cookie with nwtc, ui_site,ui_uname, ui_uid ..._ |
