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
ms.openlocfilehash: cc54664ea8ad61005de3f3fae7407946d1c861b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793850"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData 結構

為方法的執行時間資訊定義傳輸緩衝區。

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

## <a name="members"></a>Members

| 成員                       | 描述                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | 指出執行時間是否具有原生程式碼，可用於指定的方法具現化。 |
| `bIsDynamic`                 | 指出此方法是否透過輕量程式碼產生動態產生。           |
| `wSlotNumber`                | 方法資料表中的方法位置編號。                                                   |
| `NativeCodeAddr`             | 方法的初始原生位址。                                                            |
| `data`                       | 執行時間內部使用之緩衝區的指標。                                             |
| `MethodDescPtr`              | 執行時間中 `MethodDesc` 的指標。                                                     |
| `nativeCodeInfo`             | 執行時間內部用來追蹤方法之緩衝區的指標。                            |
| `moduleInfo`                 | 執行時間內部用來取得模組資訊之緩衝區的指標。                      |
| `MDToken`                    | 與指定方法相關聯的 Token。                                                         |
| `payloadGC`                  | 執行時間內部使用之垃圾收集緩衝區的指標。                          |
| `payloadGC2`                 | 執行時間內部使用之垃圾收集緩衝區的指標。                          |
| `managedDynamicMethodObject` | 如果方法是動態的，則執行時間會在內部使用此緩衝區進行資訊追蹤。     |
| `requestedIP`                | 當指定原生程式碼位址時，用來填入每個要求的結構。                    |
| `rejitDataCurrent`           | 方法的最新檢測版本的相關資訊。                                   |
| `rejitDataRequested`         | Rejit 所要求之原生位址的資訊。                                             |
| `cJittedRejitVersions`       | 透過檢測 rejitted 方法的次數。                           |

## <a name="remarks"></a>備註

這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請依照上面的指定定義結構。

## <a name="requirements"></a>需求
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
- [一般資料類型](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
