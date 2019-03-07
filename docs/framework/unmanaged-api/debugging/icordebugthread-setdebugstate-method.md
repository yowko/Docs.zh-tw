---
title: ICorDebugThread::SetDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499689"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState 方法
設定描述這個 ICorDebugThread 偵錯狀態的旗標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>參數  
 `state`  
 [in]CorDebugThreadState 列舉值，指定這個執行緒的偵錯狀態的位元組合。  
  
## <a name="remarks"></a>備註  
 `SetDebugState` 設定執行緒的目前偵錯狀態。 （如果此程序繼續執行，不實際的目前狀態 「 目前的偵錯狀態 」 表示偵錯狀態）。此設定的一般值為 THREAD_RUNNING。 偵錯工具可能會影響偵錯執行緒的狀態。 偵錯狀態執行最後的持續發生，因此如果您想要保留的執行緒，透過多個 THREAD_SUSPENDed 會繼續，您可以設定一次，並之後不需要擔心它。 暫停執行緒，並繼續處理序可能會導致死結，但它通常是不可能。 這是內建的品質的執行緒和處理序，而且是依據設計。 偵錯工具以非同步方式可以中斷和繼續執行緒，以破除死結。 如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，執行緒可能會封鎖在記憶體回收 (GC)。 這表示暫止的執行緒具有較高機率的而導致死結。 這可能不會影響偵錯事件已排入佇列。 因此在偵錯工具應該清空整個事件佇列 (藉由呼叫[icordebugcontroller:: Hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) 暫停或繼續執行緒之前。 否則，它可能認為已暫止的執行緒上取得事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
