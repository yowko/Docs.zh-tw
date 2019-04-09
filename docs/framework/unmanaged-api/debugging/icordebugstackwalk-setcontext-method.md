---
title: ICorDebugStackWalk::SetContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7306ee61d750ae256c93c049819a23d3d61f7297
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116463"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext 方法
設定組[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)有效的內容執行緒物件的目前內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>參數  
 `flag`  
 [in]A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)旗標，指出內容是從使用中框架在堆疊上，還是回溯堆疊所取得的內容。  
  
 `contextSize`  
 [in]配置的大小`CONTEXT`緩衝區。  
  
 `context`  
 [in]`CONTEXT`緩衝區。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk`成功設定物件的內容。|  
|E_FAIL|`ICorDebugStackWalk`未設定物件的內容。|  
|E_INVALIDARG|內容為 null。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|內容緩衝區是太小。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 這個方法不會更改目前執行緒的內容。  
  
 將目前的內容設定為無效的內容可能會導致無法預期的結果從堆疊查核器。  
  
 您可以擷取的位元的確切複本，此內容的立即呼叫[icordebugstackwalk:: Getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
