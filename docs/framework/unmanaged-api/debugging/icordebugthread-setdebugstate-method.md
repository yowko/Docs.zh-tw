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
ms.openlocfilehash: e28d37e4477862ff2ebeeb05ea5f5386e157cd83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678710"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState 方法

設定旗標，描述此 ICorDebugThread 的偵錯工具狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>參數  

 `state`  
 在CorDebugThreadState 列舉值的位元組合，指定此執行緒的偵錯工具狀態。  
  
## <a name="remarks"></a>備註  

 `SetDebugState` 設定執行緒目前的偵錯工具狀態。  (「目前的偵錯工具狀態」表示進程即將繼續，而非實際的目前狀態時的「偵測」狀態。 ) 這個的一般值是 THREAD_RUN。 只有偵錯工具會影響執行緒的偵錯工具狀態。 調試狀態最後會繼續執行，因此如果您想要讓執行緒 THREAD_SUSPENDed 超過多個作業，您可以將它設定為一次，之後就不必擔心。 擱置執行緒和繼續進程可能會造成鎖死，但通常不太可能發生。 這是執行緒和進程的內建品質，而且是設計的。 偵錯工具可以非同步地中斷和繼續執行緒，以中斷鎖死。 如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，則執行緒可能會封鎖垃圾收集 (GC) 。 這表示暫停的執行緒有更高的機率造成鎖死。 這可能不會影響已排入佇列的 debug 事件。 因此，偵錯工具應該在暫止或繼續執行緒之前呼叫 [ICorDebugController：： HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) ，以清空整個事件佇列 (。 否則，它可能會在已暫停的執行緒上取得事件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
