---
title: ICorDebugManagedCallback::ExitProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4518637eb47acf416a02c045f8ca6f8a90167277
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130780"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess 方法
通知偵錯工具已結束進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>參數  
 `pProcess`  
 在代表進程之 ICorDebugProcess 物件的指標。  
  
## <a name="remarks"></a>備註  
 您無法從 `ExitProcess` 事件繼續進行。 此事件可能會在進程似乎停止時，以非同步方式引發至其他事件。 如果進程在停止時終止，通常是因為某些外部的強制，就會發生這種情況。  
  
 如果 common language runtime （CLR）已經發送 managed 回呼，此事件將會延遲到該回呼傳回之後。  
  
 `ExitProcess` 事件是唯一保證會在關機時呼叫的 exit/unload 事件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
