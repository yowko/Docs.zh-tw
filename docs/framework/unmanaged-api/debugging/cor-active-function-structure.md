---
title: COR_ACTIVE_FUNCTION 結構
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: c50ba530d78296ebb956329b2f34b4f1e5cae94c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727415"
---
# <a name="cor_active_function-structure"></a>COR_ACTIVE_FUNCTION 結構

包含目前執行緒框架中正在作用的函式相關資訊。 此結構是由 [ICorDebugThread2：： GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) 方法所使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`pAppDomain`|欄位之應用程式域擁有者的指標 `ilOffset` 。|  
|`pModule`|欄位之模組擁有者的指標 `ilOffset` 。|  
|`pFunction`|欄位之函式擁有者的指標 `ilOffset` 。|  
|`ilOffset`|Microsoft 中繼語言 (MSIL) 框架位移。|  
|`flags`|保留供未來擴充性之用。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
