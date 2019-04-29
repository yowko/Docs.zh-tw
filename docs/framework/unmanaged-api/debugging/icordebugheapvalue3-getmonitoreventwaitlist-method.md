---
title: ICorDebugHeapValue3::GetMonitorEventWaitList 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db331d75244d59aacf2207a6b83a3f337a64b989
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700955"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList 方法
提供的監視器鎖定相關聯的事件的執行緒已排入佇列的已排序的清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppThreadEnum`  
 [out]ICorDebugThreadEnum 列舉程式，可用的執行緒已排序的清單。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|list 不是空的。|  
|S_FALSE|清單是空的。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 在清單中的第一個執行緒已發行的下一個呼叫的第一個執行緒<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>。 在清單中的下一個執行緒已發行下列呼叫，等等。  
  
 如果清單不是空的則這個方法會傳回 S_OK。 如果清單是空的則方法會傳回 S_FALSE。在此情況下，列舉型別是仍然有效，雖然是空的。  
  
 在任一情況下，列舉型別介面是可使用僅針對目前的同步處理狀態的持續時間。 不過，執行緒的介面從中鈔票都有效，直到執行緒結束為止。  
  
 如果`ppThreadEnum`不是有效的指標，結果為未定義。  
  
 如果發生錯誤，它無法判別，如果有的話，執行緒等候的監視器，則這個方法會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
