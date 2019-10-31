---
title: ICorDebugStackWalk::GetContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 700e0af05828b9fe0a50c1aac114e840adc276b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131855"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext 方法
傳回[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)物件中目前框架的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>參數  
 `contextFlags`  
 在旗標，指出內容緩衝區的要求內容（定義于 WinNT. h 中）。  
  
 `contextBufSize`  
 在內容緩衝區的配置大小。  
  
 `contextSize`  
 脫銷內容的實際大小。 這個值必須小於或等於內容緩衝區的大小。  
  
 `contextBuf`  
 脫銷內容緩衝區。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回目前框架的內容。|  
|E_FAIL|無法傳回內容。|  
|HRESULT_FROM_WIN32 （ERROR_INSUFFICIENT 緩衝區）|內容緩衝區太小。|  
|CORDBG_E_PAST_END_OF_STACK|框架指標已在堆疊的結尾;因此，不能存取任何其他框架。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 因為回溯只會還原暫存器的子集，例如非暫時性暫存器，所以內容可能不會完全符合呼叫時的註冊狀態。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
