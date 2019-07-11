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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4322a7e23c7085dadb3b2df6c1f72125aa685cef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756612"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法
傳回擁有此物件的監視器鎖定的 managed 的執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppThread`  
 [out]擁有此物件的監視器鎖定的 managed 的執行緒。  
  
 `pAcquisitionCount`  
 [out]此執行緒就必須釋放鎖定之前它會返回正在未擁有的次數。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|S_FALSE|沒有任何受管理的執行緒擁有此物件的監視器鎖定。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 如果 managed 的執行緒擁有此物件的監視器鎖定：  
  
- 方法會傳回 S_OK。  
  
- 執行緒物件是有效的直到執行緒結束為止。  
  
 如果沒有任何受管理的執行緒擁有這個物件的監視器鎖定`ppThread`和`pAcquisitionCount`維持不變，而方法會傳回 S_FALSE。  
  
 如果`ppThread`或`pAcquisitionCount`不是有效的指標，結果為未定義。  
  
 如果發生錯誤，無法判斷的如果有的話，執行緒擁有監視器上的鎖定這個物件，這個方法會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
