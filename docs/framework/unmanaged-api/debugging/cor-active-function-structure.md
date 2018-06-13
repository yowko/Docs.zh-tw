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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86ab3d3a0f460f1ecdf86147b14df205aaf49635
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404193"
---
# <a name="coractivefunction-structure"></a>COR_ACTIVE_FUNCTION 結構
包含目前執行緒框架中正在作用的函式相關資訊。 這個結構由[icordebugthread2:: Getactivefunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pAppDomain`|應用程式網域的擁有者的指標`ilOffset`欄位。|  
|`pModule`|模組擁有者的指標`ilOffset`欄位。|  
|`pFunction`|指標的函式擁有者`ilOffset`欄位。|  
|`ilOffset`|Microsoft intermediate language (MSIL) 位移的框架。|  
|`flags`|保留供未來擴充。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
