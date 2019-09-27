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
ms.openlocfilehash: 15e18888e307a14c4396966afc0a623e1acba104
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332816"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState 方法
設定描述此 ICorDebugThread 之偵錯工具狀態的旗標。  
  
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
 `SetDebugState` 會設定執行緒目前的「調試」狀態。 （如果進程要繼續，則為「目前的偵錯工具狀態」，而非實際的目前狀態）。此的一般值為 THREAD_RUN。 只有偵錯工具才會影響執行緒的「偵測」狀態。 Debug 狀態最後會繼續進行，因此如果您想要讓執行緒 THREAD_SUSPENDed 多次，您可以將它設定一次，之後就不需要擔心。 暫停執行緒並繼續處理可能會導致鎖死，不過通常不太可能發生。 這是執行緒和進程的內建品質，而且是依設計的。 偵錯工具可以非同步方式中斷並繼續執行緒，以中斷鎖死。 如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，則執行緒可能會封鎖垃圾收集（GC）。 這表示暫停的執行緒有更高的機率導致鎖死。 這可能不會影響已排入佇列的 debug 事件。 因此，偵錯工具應該在暫停或繼續執行緒之前，清空整個事件佇列（藉由呼叫[ICorDebugController：： HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)）。 否則，它可能會線上程上取得其認為已暫停的事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
