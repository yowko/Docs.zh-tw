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
ms.openlocfilehash: 8be7c0e32f6183deb354d8b3936ef55c2520fe9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788613"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法
傳回擁有這個物件之監視器鎖定的 managed 執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppThread`  
 脫銷擁有此物件之監視器鎖定的 managed 執行緒。  
  
 `pAcquisitionCount`  
 脫銷此執行緒在傳回為無人擁有之前，必須釋放鎖定的次數。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法已順利完成。|  
|S_FALSE|沒有受控執行緒擁有此物件上的監視鎖定。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 如果 managed 執行緒擁有此物件的監視器鎖定：  
  
- 方法會傳回 S_OK。  
  
- 執行緒物件是有效的，直到執行緒結束為止。  
  
 如果沒有 managed 執行緒擁有這個物件的監視器鎖定，`ppThread` 和 `pAcquisitionCount` 就不會變更，而且方法會傳回 S_FALSE。  
  
 如果 `ppThread` 或 `pAcquisitionCount` 不是有效的指標，則結果會是未定義的。  
  
 如果發生錯誤，因此無法判斷哪個執行緒擁有此物件的監視器鎖定，此方法會傳回表示失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
