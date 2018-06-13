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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc900ca20ac87ddecfd8f7adf0894af21ca5d2f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418086"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity 方法
告知偵錯工具執行程式碼已達到較舊版本的已編輯函式中的序列點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAppDomain`  
 [in]ICorDebugAppDomain 物件，表示應用程式定義域，其中包含編輯函式指標。  
  
 `pThread`  
 [in]表示執行緒在其發現重新對應中斷點的 ICorDebugThread 物件指標。  
  
 `pOldFunction`  
 [in]ICorDebugFunction 物件，表示目前的執行緒執行的函式版本指標。  
  
 `pNewFunction`  
 [in]ICorDebugFunction 物件，表示最新版本的函式指標。  
  
 `oldILOffset`  
 [in]指令指標的函式的舊版本中的 Microsoft intermediate language (MSIL) 位移。  
  
## <a name="remarks"></a>備註  
 此回呼會讓偵錯工具呼叫來重新對應其適當的位置中指定的函式的新版本的指令指標[icordebugilframe2:: Remapfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)方法。 如果偵錯工具不會呼叫`RemapFunction`之前先呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)方法，執行階段將會繼續執行舊的程式碼，而且會引發另一個`FunctionRemapOpportunity`回呼，在下一個序列點。  
  
 每個框架正在執行較舊版本的指定函式，直到偵錯工具傳回 S_OK 時，會叫用這個回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
