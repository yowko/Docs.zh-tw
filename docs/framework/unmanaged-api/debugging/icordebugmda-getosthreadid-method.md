---
title: ICorDebugMDA::GetOSThreadId 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: c7ab77e9316023a97d2eafe8bcccc2b45e240cd0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207828"
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId 方法
取得[ICorDebugMDA](icordebugmda-interface.md)所代表的 managed 偵錯工具（MDA）執行時所使用的作業系統（OS）執行緒識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a>參數  
 `pOsTid`  
 脫銷OS 執行緒識別碼的指標。  
  
## <a name="remarks"></a>備註  
 系統會使用 OS 執行緒而非 ICorDebugThread，以允許在原生執行緒或尚未進入 managed 程式碼的 managed 執行緒上引發 MDA 的情況。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMDA 介面](icordebugmda-interface.md)
- [使用 Managed 偵錯助理診斷錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
