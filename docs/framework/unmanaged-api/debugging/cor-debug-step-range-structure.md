---
title: COR_DEBUG_STEP_RANGE 結構
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
ms.openlocfilehash: cd85ba2e6a907ff9546614e02b4da5f45e74b924
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726635"
---
# <a name="cor_debug_step_range-structure"></a>COR_DEBUG_STEP_RANGE 結構

包含程式碼範圍的位移資訊。  
  
 此結構是由 [ICorDebugStepper：： StepRange](icordebugstepper-steprange-method.md) 方法所使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`startOffset`|範圍開頭的位移。|  
|`endOffset`|範圍結尾的位移。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StepRange 方法](icordebugstepper-steprange-method.md)
- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
