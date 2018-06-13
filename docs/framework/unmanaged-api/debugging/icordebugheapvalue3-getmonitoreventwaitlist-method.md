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
ms.openlocfilehash: a395579892ff2410865a4fcdd19cf20449b82b88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421068"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList 方法
提供與監視鎖定相關事件的執行緒已排入佇列的已排序的清單。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppThreadEnum`  
 [out]提供執行緒的已排序的清單 ICorDebugThreadEnum 列舉值。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|list 不是空的。|  
|S_FALSE|清單是空的。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 在清單中的第一個執行緒已發行的下一個呼叫的第一個執行緒<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>。 在清單中的下一個執行緒會在下列的呼叫，等發行。  
  
 如果清單不是空的則這個方法會傳回 S_OK。 如果清單是空的方法會傳回 S_FALSE。在此情況下，列舉型別是仍然有效，雖然它是空白。  
  
 在任一情況下，列舉介面是使用僅針對目前已同步處理狀態的持續時間。 不過，從它在分配的執行緒的介面都有效，直到執行緒結束為止。  
  
 如果`ppThreadEnum`不是有效的指標，結果會是未定義。  
  
 如果發生錯誤，無法判斷，如果有的話，執行緒等候的監視，方法會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
