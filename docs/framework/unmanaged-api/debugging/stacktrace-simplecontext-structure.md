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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986527"
---
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext 結構
提供可用來代替完整 `CONTEXT` 結構的簡單內容。  
  
## <a name="syntax"></a>語法  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`StackOffset`|堆疊指標或在 x86 上的 enter 堆疊指標 (ESP) 平台。|  
|`FrameOffset`|畫面格位移或 EBP 暫存器，在 x86 平台。|  
|`InstructionOffset`|指令指標或輸入指令指標 (EIP) 在 x86 平台。|  
  
## <a name="remarks"></a>備註  
 因為堆疊追蹤函式通常需要只傳回地址、 框架位移並堆疊位址，您可以選擇性地使用`SimpleContext`結構，而不是大型`CONTEXT`結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
