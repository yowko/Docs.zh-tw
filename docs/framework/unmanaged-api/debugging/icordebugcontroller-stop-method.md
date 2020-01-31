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
ms.openlocfilehash: 3a107176e48a88a0a04534f7044c1e416caf4091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788886"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop 方法
在進程中執行 managed 程式碼的所有線程上執行合作性停止。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwTimeoutIgnored`  
 未使用。  
  
## <a name="remarks"></a>備註  
 `Stop` 會在進程中執行 managed 程式碼的所有線程上執行合作的停止。 在僅限 managed 的偵錯工具期間，非受控執行緒可能會繼續執行（但在嘗試呼叫 managed 程式碼時將會遭到封鎖）。 在 interop 偵錯工具期間，非受控執行緒也會停止。 目前已忽略 `dwTimeoutIgnored` 值，並將其視為無限（-1）。 如果合作性停止因鎖死而失敗，則會暫止所有的執行緒，並傳回 E_TIMEOUT。  
  
> [!NOTE]
> `Stop` 是調試 API 中唯一的同步方法。 當 `Stop` 傳回 S_OK 時，進程就會停止。 未提供回呼以通知接聽程式停止。 偵錯工具必須呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md) ，以允許進程繼續執行。  
  
 偵錯工具會維護一個停止計數器。 當計數器變成零時，控制器就會繼續。 每次呼叫 `Stop` 或每個分派的回呼都會遞增計數器。 `ICorDebugController::Continue` 的每個呼叫都會遞減計數器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
