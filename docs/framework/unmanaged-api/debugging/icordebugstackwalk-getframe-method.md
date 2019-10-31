---
title: ICorDebugStackWalk::GetFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131831"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame 方法
取得[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件中的目前框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>參數  
 `pFrame`  
 在建立之框架物件位址的指標，表示堆疊中目前的框架。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|執行時間已成功傳回目前的框架。|  
|E_FAIL|未傳回目前的框架。|  
|S_FALSE|目前的框架是原生堆疊框架。|  
|E_INVALIDARG|`pFrame` 為 null。|  
|CORDBG_E_PAST_END_OF_STACK|框架指標已在堆疊的結尾;因此，不能存取任何其他框架。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 `ICorDebugStackWalk` 只會傳回實際的堆疊框架。 請使用[ICorDebugThread3：： GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)方法來傳回內部框架。 （內部畫面是由執行時間推送至堆疊的資料結構，用來儲存暫存資料）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugStackWalk 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
