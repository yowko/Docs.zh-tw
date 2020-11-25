---
title: ICorDebugManagedCallback2::FunctionRemapComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: 7eb7fb55a5077d2914eb85a67ca62163a1aa8cc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704587"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a>ICorDebugManagedCallback2::FunctionRemapComplete 方法

通知偵錯工具程式碼執行已切換至新版本的編輯函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a>參數  

 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，代表包含已編輯函式的應用程式域。  
  
 `pThread`  
 在ICorDebugThread 物件的指標，代表遇到重新對應中斷點的執行緒。  
  
 `pFunction`  
 在ICorDebugFunction 物件的指標，表示執行緒上目前正在執行的函式版本。  
  
## <a name="remarks"></a>備註  

 此回呼讓偵錯工具有機會重新建立先前存在的任何 steppers。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
