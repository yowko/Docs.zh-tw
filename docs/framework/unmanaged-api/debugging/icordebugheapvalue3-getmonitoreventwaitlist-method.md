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
ms.openlocfilehash: 0fbff178efd4d0dff3593907b3d40e946be2ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121301"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList 方法
提供在與監視器鎖定相關聯的事件上排入佇列之執行緒的已排序清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppThreadEnum`  
 脫銷提供執行緒之已排序清單的 ICorDebugThreadEnum 列舉值。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|list 不是空的。|  
|S_FALSE|清單是空的。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 清單中的第一個執行緒是 <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>下一次呼叫所釋放的第一個執行緒。 清單中的下一個執行緒會在下列呼叫中釋放，依此類推。  
  
 如果清單不是空的，則這個方法會傳回 S_OK。 如果清單是空的，方法會傳回 S_FALSE;在此情況下，列舉仍然有效，但它是空的。  
  
 在任一情況下，列舉介面僅適用于目前已同步處理狀態的持續時間。 不過，從它所分配的執行緒介面是有效的，直到執行緒結束為止。  
  
 如果 `ppThreadEnum` 不是有效的指標，則結果會是未定義的。  
  
 如果發生錯誤，因此無法判斷線程是否正在等候監視器，此方法會傳回表示失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
