---
title: "ICorDebugController::Stop 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b92d07f8d162123d20c6861d204d73789060906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop 方法
在 managed 程式碼執行處理序中的所有執行緒上執行合作式停止。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwTimeoutIgnored`  
 未使用。  
  
## <a name="remarks"></a>備註  
 `Stop`會執行合作式停止執行的所有執行緒在 managed 程式碼中處理程序。 僅限 managed 偵錯工作階段，unmanaged 的執行緒可能會繼續執行 （但是將會封鎖嘗試呼叫 managed 程式碼時）。 在 interop 偵錯工作階段，unmanaged 的執行緒也將會停止。 `dwTimeoutIgnored`值目前已忽略，並且視為 INFINITE (-1)。 由於死結合作式的停駐點時，所有執行緒都會都暫停，並傳回 E_TIMEOUT。  
  
> [!NOTE]
>  `Stop`是偵錯 API 中的只同步方法。 當`Stop`傳回 S_OK 時，處理程序已停止。 通知停駐點的接聽程式會不提供任何回呼。 偵錯工具必須呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)允許繼續執行的程序。  
  
 偵錯工具會維持停止計數器。 當計數器為零，控制器會繼續執行。 每次呼叫`Stop`或每個分派的回呼會遞增計數器。 每次呼叫`ICorDebugController::Continue`遞減的計數器。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 
