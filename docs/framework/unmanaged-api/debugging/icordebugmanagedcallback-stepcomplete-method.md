---
title: ICorDebugManagedCallback::StepComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
ms.openlocfilehash: 8de0858abe7db9ae1225f449083e417e13507b3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703033"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a>ICorDebugManagedCallback::StepComplete 方法

通知偵錯工具已完成步驟。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a>參數  

 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，該物件代表包含步驟已完成之執行緒的應用程式域。  
  
 `pThread`  
 在ICorDebugThread 物件的指標，該物件表示步驟已完成的執行緒。  
  
 `pStepper`  
 在ICorDebugStepper 物件的指標，代表程式碼執行中的步驟。  
  
 `reason`  
 在CorDebugStepReason 列舉的值，表示個別步驟的結果。  
  
## <a name="remarks"></a>備註  

 如果需要，可以使用分檔器繼續逐步執行，除非偵錯工具已終止。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
