---
title: ECustomDumpFlavor 列舉
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 1b8440ed6e878aac3dd08d9f8ed528c93739a724
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686315"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor 列舉

包含值，這些值會指出在報告錯誤時，要在堆積傾印的自訂子集中包含哪些專案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|指定自訂堆積傾印應以小型傾印開頭，並包含任何傳遞至相同方法的 [CustomDumpItem](customdumpitem-structure.md) 實例所指定的額外資料。|  
|`DUMP_FLAVOR_NonHeapCLRState`|指定自訂堆積傾印應該收集並非動態配置的所有執行時間狀態資料。|  
  
## <a name="remarks"></a>備註  

 型別的參數 `ECustomDumpFlavor` 會傳遞至 [ICLRErrorReportingManager：： BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) 方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ECustomDumpItemKind 列舉](ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager 介面](iclrerrorreportingmanager-interface.md)
- [裝載列舉](hosting-enumerations.md)
