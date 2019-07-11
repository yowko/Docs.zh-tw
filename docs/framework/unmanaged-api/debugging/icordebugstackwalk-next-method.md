---
title: ICorDebugStackWalk::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6c96e64b1197b5762c0ad7dbed5458b5d71a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760900"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next 方法
移動[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)下一個畫面格的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|執行階段成功回溯至下一個畫面 （請參閱 < 備註 >）。|  
|E_FAIL|`ICorDebugStackWalk`物件不可以進階。|  
|CORDBG_S_AT_END_OF_STACK|堆疊的結尾已到達此回溯的結果。|  
|CORDBG_E_PAST_END_OF_STACK|框架指標已經結尾的堆疊;因此，可以不存取任何其他的框架。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 `Next`方法的進展`ICorDebugStackWalk`物件至呼叫端的框架，只有當執行階段可以回溯目前的框架。 否則，物件會前進至下一個框架執行階段可回溯。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugStackWalk 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
