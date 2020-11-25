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
ms.openlocfilehash: 21bf0122039a720ff8a1d38d62e77c2560dcc435
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726531"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList 方法

提供已排序的執行緒清單，這些執行緒會排入與監視器鎖定相關聯的事件上。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppThreadEnum`  
 擴展提供已排序之執行緒清單的 ICorDebugThreadEnum 列舉值。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|list 不是空的。|  
|S_FALSE|清單是空的。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  

 清單中的第一個執行緒是下一次呼叫時所釋放的第一個執行緒 <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> 。 清單中的下一個執行緒會在下列呼叫中釋放，依此類推。  
  
 如果清單不是空的，這個方法會傳回 S_OK。 如果清單是空的，則方法會傳回 S_FALSE;在此情況下，列舉仍然有效，但它是空的。  
  
 在任一種情況下，列舉介面只能在目前已同步處理狀態的持續時間內使用。 不過，線上程結束之前，從它進行分配的執行緒介面會是有效的。  
  
 如果不是 `ppThreadEnum` 有效的指標，則結果為未定義。  
  
 如果發生錯誤，導致無法判斷線程（如果有的話）正在等待監視器，則方法會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
