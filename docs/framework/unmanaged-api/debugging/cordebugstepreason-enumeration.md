---
title: CorDebugStepReason 列舉
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 50903b3737c0fc63eda2b1190e4c3d961ce3ae7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726037"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason 列舉

指出個別步驟的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`STEP_NORMAL`|在相同的函式中，以正常方式完成的逐步執行。|  
|`STEP_RETURN`|在函式傳回之後，正常地繼續執行。|  
|`STEP_CALL`|在新呼叫的函式開始時，正常地繼續執行。|  
|`STEP_EXCEPTION_FILTER`|產生例外狀況，並將控制權傳遞給例外狀況篩選準則。|  
|`STEP_EXCEPTION_HANDLER`|產生例外狀況，並將控制權傳遞給例外狀況處理常式。|  
|`STEP_INTERCEPT`|控制項已傳遞至攔截器。|  
|`STEP_EXIT`|在步驟完成之前，執行緒已結束。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [StepComplete 方法](icordebugmanagedcallback-stepcomplete-method.md)
- [偵錯列舉](debugging-enumerations.md)
