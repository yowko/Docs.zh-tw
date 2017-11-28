---
title: "CorDebugChainReason 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d501db111256861a3d0a602712e4c32f40b7b6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason 列舉
指出呼叫鏈結初始化的原因。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`CHAIN_NONE`|未起始任何呼叫鏈結。|  
|`CHAIN_CLASS_INIT`|鏈結是由建構函式所起始。|  
|`CHAIN_EXCEPTION_FILTER`|鏈結是由例外狀況篩選條件所起始。|  
|`CHAIN_SECURITY`|鏈結是由強制執行安全性的程式碼所起始。|  
|`CHAIN_CONTEXT_POLICY`|鏈結是由內容原則所起始。|  
|`CHAIN_INTERCEPTION`|未使用。|  
|`CHAIN_PROCESS_START`|未使用。|  
|`CHAIN_THREAD_START`|鏈結是由執行緒執行開始所起始。|  
|`CHAIN_ENTER_MANAGED`|鏈結是由進入 Managed 程式碼的項目所起始。|  
|`CHAIN_ENTER_UNMANAGED`|鏈結是由進入 Unmanaged 程式碼的項目所起始。|  
|`CHAIN_DEBUGGER_EVAL`|未使用。|  
|`CHAIN_CONTEXT_SWITCH`|未使用。|  
|`CHAIN_FUNC_EVAL`|鏈結是由函式評估所起始。|  
  
## <a name="remarks"></a>備註  
 使用[icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法來確定呼叫鏈結的起始原因。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
