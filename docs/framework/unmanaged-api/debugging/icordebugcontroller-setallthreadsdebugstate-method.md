---
title: ICorDebugController::SetAllThreadsDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976586"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState 方法
設定進程中所有 managed 執行緒的偵錯工具狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>參數  
 `state`  
 在"CorDebugThreadState" 列舉的值，指定要進行偵錯工具的執行緒狀態。  
  
 `pExceptThisThread`  
 在"ICorDebugThread" 物件的指標，代表要從 debug 狀態設定中豁免的執行緒。 如果此值為 null，則不會豁免任何執行緒。  
  
## <a name="remarks"></a>備註  
 方法可能會影響不是透過[EnumerateThreads 方法](icordebugcontroller-enumeratethreads-method.md)顯示的執行緒，因此使用`SetAllThreadsDebugState`方法暫停的執行緒將需要使用`SetAllThreadsDebugState`方法繼續。 `SetAllThreadsDebugState`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
