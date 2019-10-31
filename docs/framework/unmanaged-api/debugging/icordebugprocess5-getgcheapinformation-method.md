---
title: ICorDebugProcess5::GetGCHeapInformation 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 3aa9fe884b16a239f5105dd262edeb8fc3e4abaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084411"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation 方法
提供有關垃圾收集堆積的一般資訊，包括目前是否可列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a>參數  
 `pHeapInfo`  
 脫銷[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)值的指標，提供有關垃圾收集堆積的一般資訊。  
  
## <a name="remarks"></a>備註  
 在列舉堆積或個別堆積區域之前，必須先呼叫 `ICorDebugProcess5::GetGCHeapInformation` 方法，以確保進程中的垃圾收集結構目前有效。 當集合正在進行時，無法逐步執行垃圾收集堆積。 否則，列舉可能會捕捉到不正確垃圾收集結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
