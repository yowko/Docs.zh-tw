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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20833624b4b853a1a56964e11a25f446c6b39053
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId 方法
取得作業系統 (OS) 執行緒識別項所代表的 managed 偵錯助理 (MDA) [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)正在執行。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pOsTid`  
 [out]作業系統執行緒的識別碼指標。  
  
## <a name="remarks"></a>備註  
 作業系統執行緒而不是 ICorDebugThread 用於允許在原生執行緒或尚未輸入 managed 程式碼，managed 執行緒上，會引發 MDA 的情況下。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugMDA 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
