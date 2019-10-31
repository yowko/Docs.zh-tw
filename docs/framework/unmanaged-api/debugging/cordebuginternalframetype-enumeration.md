---
title: CorDebugInternalFrameType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: e76800316885c27c697421d454341d5f0789c611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097957"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType 列舉
識別堆疊框架的類型。 [ICorDebugInternalFrame：： GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)方法會使用這個列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`STUBFRAME_NONE`|null 值。 `ICorDebugInternalFrame::GetFrameType` 方法永遠不會傳回此值。|  
|`STUBFRAME_M2U`|受管理的非受控 stub 框架。|  
|`STUBFRAME_U2M`|未受管理的非受控 stub 框架。|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|應用程式域之間的轉換。|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|輕量方法呼叫。|  
|`STUBFRAME_FUNC_EVAL`|函數評估的開始。|  
|`STUBFRAME_INTERNALCALL`|Common language runtime 的內部呼叫。|  
|`STUBFRAME_CLASS_INIT`|類別初始化的起始。|  
|`STUBFRAME_EXCEPTION`|擲回的例外狀況。|  
|`STUBFRAME_SECURITY`|用於代碼啟用安全性的框架。|  
|`STUBFRAME_JIT_COMPILATION`|執行時間會以 JIT 方式編譯方法。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
