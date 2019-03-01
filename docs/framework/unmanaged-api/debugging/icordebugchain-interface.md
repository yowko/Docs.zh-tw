---
title: ICorDebugChain 介面
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb21712066e7b351e974a66f61ec0326a110aed6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982033"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain 介面

表示實體或邏輯呼叫堆疊的區段。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateFrames 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|取得列舉值，其中包含所有的受管理的堆疊框架，在鏈結中，從最新的框架開始。|  
|[GetActiveFrame 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|取得使用 (也就是最新) 鏈結上的框架。|  
|[GetCallee 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|取得這個鏈結所呼叫函式鏈結。|  
|[GetCaller 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|取得呼叫這個接收鏈結的鏈結。|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|未實作。|  
|[GetNext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|取得執行緒中的下一個框架鏈結。|  
|[GetPrevious 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|取得執行緒先前的框架鏈結。|  
|[GetReason 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|取得這個呼叫鏈結發生的原因。|  
|[GetRegisterSet 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|取得設定此鏈結的使用中部分的暫存器。|  
|[GetStackRange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|取得這個鏈結的堆疊區段的位址範圍。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|取得實體的執行緒，此呼叫鏈結的一部分。|  
|[IsManaged 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|取得值，指出這個鏈結是否正在執行的 managed 程式碼。|  
  
## <a name="remarks"></a>備註  
 鏈結中的堆疊框架會佔據連續的堆疊空間，並共用相同的執行緒和內容。 鏈結可能代表其中一個 managed 或 unmanaged 程式碼鏈結。 空白`ICorDebugChain`執行個體代表 unmanaged 程式碼鏈結。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
