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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05184ceb3b32eb003951fff5cfdfbfb813992552
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792856"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType 列舉
識別堆疊框架的類型。 這個列舉型別由[icordebuginternalframe:: Getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`STUBFRAME_NONE`|null 值。 `ICorDebugInternalFrame::GetFrameType`方法不會傳回此值。|  
|`STUBFRAME_M2U`|Managed 至 unmanaged 虛設常式的框架。|  
|`STUBFRAME_U2M`|非受控至 managed 虛設常式的框架。|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|應用程式定義域之間的轉換。|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|輕量的方法呼叫。|  
|`STUBFRAME_FUNC_EVAL`|函式評估的開始。|  
|`STUBFRAME_INTERNALCALL`|Common language runtime 內部呼叫。|  
|`STUBFRAME_CLASS_INIT`|在類別初始化開始。|  
|`STUBFRAME_EXCEPTION`|就會擲回例外狀況。|  
|`STUBFRAME_SECURITY`|用於程式碼存取安全性的框架。|  
|`STUBFRAME_JIT_COMPILATION`|執行階段是 JIT 編譯方法。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
