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
ms.openlocfilehash: d8375948be5820aaf6e879b82bcfde6471cccf3f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679893"
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
 在"CorDebugThreadState" 列舉值，這個值會指定要進行偵錯工具之執行緒的狀態。  
  
 `pExceptThisThread`  
 在"ICorDebugThread" 物件的指標，代表要從「偵測狀態」設定中豁免的執行緒。 如果這個值為 null，則不會豁免任何執行緒。  
  
## <a name="remarks"></a>備註  

 此 `SetAllThreadsDebugState` 方法可能會影響不會透過 [EnumerateThreads 方法](icordebugcontroller-enumeratethreads-method.md)顯示的執行緒，因此使用該方法暫停的執行緒必須 `SetAllThreadsDebugState` 以方法繼續執行 `SetAllThreadsDebugState` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
