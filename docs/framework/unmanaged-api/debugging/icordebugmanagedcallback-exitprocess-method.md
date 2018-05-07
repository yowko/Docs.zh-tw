---
title: ICorDebugManagedCallback::ExitProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42330296defe90980dd431ce39765a549057b82a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess 方法
告知偵錯工具的處理序已經結束。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProcess`  
 [in]ICorDebugProcess 物件代表處理程序的指標。  
  
## <a name="remarks"></a>備註  
 您無法繼續從`ExitProcess`事件。 其他事件，而要停止的處理程序會出現此事件可能會以非同步方式引發。 如果在處理序終止時停止，通常是因為某些外部的強制，也可能會發生。  
  
 如果 common language runtime (CLR) 已分派 managed 回撥，則此事件將會延遲，直到該回呼傳回之後。  
  
 `ExitProcess`事件是只保證在關閉呼叫結束/卸載事件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
