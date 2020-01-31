---
title: CorDebugIntercept 列舉
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 8ce48b63a92e84ce92da0dcf35a6242744c1a8c3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778423"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept 列舉
表示可以攔截這類型的程式碼 (也就是逐步執行)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`INTERCEPT_NONE`|無法攔截任何程式碼。|  
|`INTERCEPT_CLASS_INIT`|可以攔截建構函式。|  
|`INTERCEPT_EXCEPTION_FILTER`|可以攔截例外狀況篩選條件。|  
|`INTERCEPT_SECURITY`|可以攔截會強制執行安全性的程式碼。|  
|`INTERCEPT_CONTEXT_POLICY`|可以攔截內容原則。|  
|`INTERCEPT_INTERCEPTION`|未使用。|  
|`INTERCEPT_ALL`|可以攔截所有的程式碼。|  
  
## <a name="remarks"></a>備註  
 請使用[ICorDebugStepper：： SetInterceptMask](icordebugstepper-setinterceptmask-method.md)方法來建立可攔截的程式碼類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
