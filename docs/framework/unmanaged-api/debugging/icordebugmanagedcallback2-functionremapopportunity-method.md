---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
ms.openlocfilehash: c6c361113a441df050a8e7cd5219819cc8332581
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131485"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity 方法
通知偵錯工具程式碼執行已到達較舊版本的已編輯函式中的序列點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，表示包含已編輯之函數的應用程式域。  
  
 `pThread`  
 在ICorDebugThread 物件的指標，代表發生重新對應中斷點的執行緒。  
  
 `pOldFunction`  
 在ICorDebugFunction 物件的指標，代表目前正線上程上執行的函式版本。  
  
 `pNewFunction`  
 在ICorDebugFunction 物件的指標，表示函式的最新版本。  
  
 `oldILOffset`  
 在舊版函式中的指令指標之 Microsoft 中繼語言（MSIL）位移。  
  
## <a name="remarks"></a>備註  
 這個回呼會藉由呼叫[ICorDebugILFrame2：： RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)方法，讓偵錯工具有機會將指令指標重新對應至指定函式的新版本中的適當位置。 如果偵錯工具在呼叫[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法之前不會呼叫 `RemapFunction`，執行時間將會繼續執行舊的程式碼，並會在下一個序列點引發另一個 `FunctionRemapOpportunity` 回呼。  
  
 針對執行舊版指定函式的每個框架，會叫用此回呼，直到偵錯工具傳回 S_OK 為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
