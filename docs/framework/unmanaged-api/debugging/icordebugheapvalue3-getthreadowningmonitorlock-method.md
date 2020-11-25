---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: fef0902aedbcd8572d2dc67fae7927f754af4489
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723307"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法

傳回在這個物件上擁有監視器鎖定的 managed 執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppThread`  
 擴展擁有此物件之監視器鎖定的 managed 執行緒。  
  
 `pAcquisitionCount`  
 擴展這個執行緒在回到無人擁有之前，必須釋放鎖定的次數。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|S_FALSE|沒有 managed 執行緒擁有此物件的監視器鎖定。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  

 如果 managed 執行緒擁有此物件的監視器鎖定：  
  
- 方法會傳回 S_OK。  
  
- 執行緒物件會一直有效，直到執行緒結束為止。  
  
 如果沒有 managed 執行緒擁有此物件的監視器鎖定，而且沒有變更 `ppThread` `pAcquisitionCount` ，則方法會傳回 S_FALSE。  
  
 如果 `ppThread` 或不是 `pAcquisitionCount` 有效的指標，則結果為未定義。  
  
 如果發生錯誤，導致無法判斷線程（如果有的話）擁有此物件的監視器鎖定，方法會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
