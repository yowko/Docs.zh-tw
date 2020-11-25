---
title: DacpMethodDescData 結構
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: dcf01c00a106c131646a16597dca4092a06c5983
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723060"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData 結構

定義方法執行時間資訊的傳輸緩衝區。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>成員

| member                       | 描述                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | 指出執行時間是否有原生程式碼可用於方法的指定具現化。 |
| `bIsDynamic`                 | 指出方法是否透過輕量程式碼產生動態產生。           |
| `wSlotNumber`                | 方法資料表中的方法位置號碼。                                                   |
| `NativeCodeAddr`             | 方法的初始原生位址。                                                            |
| `data`                       | 執行時間內部使用之緩衝區的指標。                                             |
| `MethodDescPtr`              | 執行時間中的指標 `MethodDesc` 。                                                     |
| `nativeCodeInfo`             | 執行時間在內部用來追蹤方法的緩衝區指標。                            |
| `moduleInfo`                 | 執行時間用於模組資訊的緩衝區指標。                      |
| `MDToken`                    | 與指定方法相關聯的 Token。                                                         |
| `payloadGC`                  | 執行時間內部使用的垃圾收集緩衝區指標。                          |
| `payloadGC2`                 | 執行時間內部使用的垃圾收集緩衝區指標。                          |
| `managedDynamicMethodObject` | 如果是動態方法，則執行時間會在內部使用此緩衝區來追蹤資訊。     |
| `requestedIP`                | 在指定機器碼位址時，用來填入每個要求的結構。                    |
| `rejitDataCurrent`           | 方法最新檢測版本的相關資訊。                                   |
| `rejitDataRequested`         | Rejit 所要求之原生位址的資訊。                                             |
| `cJittedRejitVersions`       | 透過檢測 rejitted 方法的次數。                           |

## <a name="remarks"></a>備註

此結構存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請依照上述指定的方式定義結構。

## <a name="requirements"></a>需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
**標頭：** 沒有  
連結 **庫：** 沒有  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
- [常見資料類型](../common-data-types-unmanaged-api-reference.md)
