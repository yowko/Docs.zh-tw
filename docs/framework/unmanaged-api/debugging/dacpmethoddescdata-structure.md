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
ms.openlocfilehash: 567dc3942f79b6bfd29338b9103083aa64e66451
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203193"
---
# <a name="dacpmethoddescdata-structure"></a>DacpMethodDescData 結構

定義方法的執行階段資訊的傳輸緩衝區。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```
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

| 成員                       | 描述                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | 指出執行階段是否有原生程式碼可用於指定具現化的方法。 |
| `bIsDynamic`                 | 指出是否透過輕量型程式碼產生動態產生的方法。           |
| `wSlotNumber`                | 方法的方法資料表中的位置編號。                                                   |
| `NativeCodeAddr`             | 方法的初始原生位址。                                                            |
| `data`                       | 供內部使用執行階段緩衝區的指標。                                             |
| `MethodDescPtr`              | 指標`MethodDesc`在執行階段。                                                     |
| `nativeCodeInfo`             | 若要追蹤方法內部使用執行階段緩衝區的指標。                            |
| `moduleInfo`                 | 執行階段內部使用的模組資訊之緩衝區的指標。                      |
| `MDToken`                    | 與指定的方法相關聯的權杖。                                                         |
| `payloadGC`                  | 供內部使用執行階段的記憶體回收集合緩衝區的指標。                          |
| `payloadGC2`                 | 供內部使用執行階段的記憶體回收集合緩衝區的指標。                          |
| `managedDynamicMethodObject` | 如果方法是動態的執行階段會使用這個緩衝區內部追蹤的資訊。     |
| `requestedIP`                | 用來填入每個要求時的原生程式碼位址結構。                    |
| `rejitDataCurrent`           | 方法的最新的已檢測版本的相關資訊。                                   |
| `rejitDataRequested`         | Rejit 要求的原生位址資訊。                                             |
| `cJittedRejitVersions`       | 此方法已透過檢測 rejitted 的次數。                           |

## <a name="remarks"></a>備註

此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。 若要使用它，定義如上述所指定的結構。

## <a name="requirements"></a>需求
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** None  
**LIBRARY:** None  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [一般資料類型](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
