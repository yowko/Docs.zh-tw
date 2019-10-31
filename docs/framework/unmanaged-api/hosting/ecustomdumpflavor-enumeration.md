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
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124921"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor 列舉
包含值，指出報告錯誤時，要包含在堆積傾印的自訂子集中的專案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|指定自訂堆積傾印應啟動為小型傾印，並包含傳遞至相同方法之任何[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)實例所指定的額外資料。|  
|`DUMP_FLAVOR_NonHeapCLRState`|指定自訂堆積傾印應收集所有未動態配置的執行時間狀態資料。|  
  
## <a name="remarks"></a>備註  
 `ECustomDumpFlavor` 類型的參數會傳遞至[ICLRErrorReportingManager：： BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ECustomDumpItemKind 列舉](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [ICLRErrorReportingManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
