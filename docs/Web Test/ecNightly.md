---
title: EC_NIGHTLY
---
## Happy-member

For Each run test

| Param           | Size | Remark                                    | dow |
| --------------- | ---- | ----------------------------------------- | --- |
| langCode        | 3→2  | ignored en_Us, hence real size = 2        |     |
| shopTypes       | 2    | Optionally specified by env.SHOP_TYPE     |     |
| users           | 1    | Specified MEMBER                          |     |
| routes          | 2    | Optionally specified by env.ROUTE_TYPE    |     |
| deliveryOption  | 4→1  | SELF_PICKUP is excluded only in Sanity/CI | [x] |
| areaOption      | 3→1  | KOWLOON is excluded in sanity             | [x] |
| receiverList    | 1    | `newReceiverDefault`                      |     |
| codeListToFuncs | 131  |                                           |     |

### CodeListToFuncs

| Elements               | CodeList | total(Web) | total(Msite) |
| ---------------------- | -------- | ---------- | ------------ |
| sharedCodeListToFunc   | 15       | 49         | 44           |
| memberCommonListToFunc | 2        | 36         | 30           |
| errorMemberCodes       | 1        | 1          | 1            |
| receiverLimitCodes     | 1        | 1          | 1            |
|                        |          | 87         | 76           |

#### sharedCodeListToFunc

| CodeList                                           | size | verifyCC | verifyQR  | verifyP | qrTypes | contribute (WEB) |
| -------------------------------------------------- | ---- | -------- | --------- | ------- | ------- | ---------------- |
| noPromoCodes                                       | 1    | [x]      | [x]       | [ ]     | 5 / 4   | 1 + 1×5 = 6      |
| cardOnlyCodes                                      | 2    | [x]      | [ ]       | [x]     | 1       | 2×1+1 = 3        |
| alipayOnlyCodes                                    | 2    | [ ]      | [x]       | [x]     | 1       | 2×1+1 = 3        |
| wechatOnlyCodes(disabled)                          | 2    | [ ]      | [x]       | [x]     | 1       | 0                |
| paymeOnlyCodes                                     | 2    | [ ]      | [x]       | [x]     | 1       | 2×1+1 = 3        |
| octopusOnlyCodes                                   | 2    | [ ]      | [x]       | [x]     | 1       | 2×1+1 = 3        |
| merchantOnlyCodes                                  | 2    | [x]      | [x]       | [ ]     | 5 / 4   | 2×1+2×5 = 12     |
| msiteOnlyCodes                                     | 2    | [x]      | [x]       | [x]     | 4       | 2×1+2×4 + 1= 11  |
| webOnlyCodes                                       | 2    | [x]      | [x]       | [x]     | 5       | 2×1+2×5 + 1= 13  |
| errorWebCodes                                      | 2    | [ ]      | [ ]       | [x]     |         | 1                |
| errorMsiteCodes                                    | 2    | [ ]      | [ ]       | [x]     |         | 1                |
| [errorMerchantCodes](dowEcN.md#errorMerchantCodes) | 16   | [ ]      | [ ]       | [x]     |         | 1                |
| [wrongMerchantCodes](dowEcN.md#wrongMerchantCodes) | 20   | [ ]      | [ ]       | [x]     |         | 1                |
| [wrongProductCodes](dowEcN#wrongProductCodes)      | 18   | [ ]      | [ ]       | [x]     |         | 1                |
| [errorAllCodes](dowEcN#errorAllCodes)              | 14   | [ ]      | [ ]       | [x]     |         | 1                |
| WEB Total                                          |      | 3×2+1=7  | 13×2+5=31 | 11      |         | 49               |
| MSITE Total                                        |      | 3×2+1=7  | 11×2+4=26 | 11      |         | 44               |

#### memberCommonListToFunc

| CodeList         | size | verifyCC | verifyQR     | qrTypes | contribute (WEB) | Remark  |
| ---------------- | ---- | -------- | ------------ | ------- | ---------------- | ------- |
| memberOnlyCodes  | 2    | [x]      | [x]          | 5 / 4   | 2×1 + 2×5 = 12   |         |
| productOnlyCodes | 4    | [x]      | [x]          | 5 / 4   | 4×1 + 4×5 = 24   | only EC |
| WEB Total        |      | 2+4 = 6  | 2×5+4×5 = 30 |         | 36               |         |
| MSITE Total      |      | 2+4 = 6  | 2×4+4×4 = 24 |         | 30               |         |

#### Other

| CodeList           | size                | verifyP | contribute |
| ------------------ | ------------------- | ------- | ---------- |
| errorMemberCodes   | dow(dow(8,5) + 2,5) | [x]     | 1          |
| receiverLimitCodes | 2                   | [x]     | 1          |


# Conclusion

Test cases for happy-member (Web)
```
LangCodes(2) × ShopTypes(2) × users (1) × routes(2) × deliveryOption(1) × areaOption(1) × receiverList(1) × codeListToFuncs(87) (13 + 61 + 13)
= 696

productOnlyCodes(Only EC) = LangCodes(2) × ShopTypes = PS(1) × users (1) × routes(2) × deliveryOption(1) × areaOption(1) × receiverList(1) × codeListToFuncs(24) = 96

Total = 696-96 = 600 (excluding skips) For Web
104 Verify P + 408 QrCode + 88 Verify CC
```

Test cases for happy-member (MSite)
```
LangCodes(2) × ShopTypes(2) × users (1) × routes(2) × deliveryOption(1) × areaOption(1) × receiverList(1) × codeListToFuncs(76) 
= 608

productOnlyCodes(Only EC) = LangCodes(2) × ShopTypes = PS(1) × users (1) × routes(2) × deliveryOption(1) × areaOption(1) × receiverList(1) × codeListToFuncs(20) = 80

Total = 608-80 = 528 (excluding skips) For Msite
104 Verify P + 336 QrCode + 88 Verify CC
```