---
title: ICorDebugController::Stop 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db8c5c8dbb5bf3ff8bc7202a60397180b7b38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183387"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop 方法
在此程序中執行 managed 程式碼的所有執行緒上執行合作式的停駐點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwTimeoutIgnored`  
 未使用。  
  
## <a name="remarks"></a>備註  
 `Stop` 處理序中，會執行合作式停止執行的所有執行緒上受管理程式碼。 僅限 managed 偵錯工作階段期間，未受管理的執行緒可能會繼續執行 （但會被封鎖，嘗試呼叫 managed 程式碼時）。 在 interop 偵錯工作階段中，也將停止未受管理的執行緒。 `dwTimeoutIgnored`目前會忽略並視為無限 (-1) 值。 如果由於死結之故，失敗的合作式的停駐點，所有執行緒都會都暫停，並傳回 E_TIMEOUT。  
  
> [!NOTE]
>  `Stop` 是偵錯 API 中只同步的方法。 當`Stop`傳回 s_ok 時，此程序已停止。 通知停駐點的接聽程式會不提供任何回呼。 偵錯工具必須呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)允許繼續執行的程序。  
  
 偵錯工具會維持停止的計數器。 計數器歸零時，則控制器會繼續。 每次呼叫`Stop`或每個分派的回呼遞增的計數器。 每次呼叫`ICorDebugController::Continue`遞減計數器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
