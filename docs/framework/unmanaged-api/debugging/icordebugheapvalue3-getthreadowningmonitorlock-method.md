---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法
傳回擁有此物件的監視器鎖定的 managed 的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppThread`  
 [out]擁有此物件的監視器鎖定的 managed 的執行緒。  
  
 `pAcquisitionCount`  
 [out]必須解除鎖定，再傳回所未擁有這個執行緒的次數。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|S_FALSE|沒有受管理的執行緒擁有此物件的監視器鎖定。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 如果 managed 的執行緒擁有此物件的監視器鎖定：  
  
-   方法會傳回 S_OK。  
  
-   執行緒物件是有效，直到執行緒結束為止。  
  
 如果任何受管理的執行緒不擁有此物件的監視器鎖定`ppThread`和`pAcquisitionCount`維持不變，而且方法會傳回 S_FALSE。  
  
 如果`ppThread`或`pAcquisitionCount`不是有效的指標，結果會是未定義。  
  
 如果發生錯誤，使它無法判別其執行緒的話，擁有這個物件的監視器鎖定方法會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
