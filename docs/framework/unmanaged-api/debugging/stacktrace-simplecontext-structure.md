---
title: StackTrace_SimpleContext 結構
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 1cd3c34fc292e4a050fa8a75078283e34425fc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139122"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext 結構
提供可用來代替完整 `CONTEXT` 結構的簡單內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`StackOffset`|堆疊指標，或 x86 平臺上的輸入堆疊指標（ESP）。|  
|`FrameOffset`|框架位移，或 x86 平臺上的 EBP 暫存器。|  
|`InstructionOffset`|指令指標，或 x86 平臺上的 enter 指令指標（EIP）。|  
  
## <a name="remarks"></a>備註  
 因為堆疊追蹤函數通常只需要傳回位址、框架位移和堆疊位址，所以您可以選擇性地使用 `SimpleContext` 結構，而不是大型的 `CONTEXT` 結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
