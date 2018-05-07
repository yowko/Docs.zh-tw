---
title: ICorDebugProcess::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9ed79eb799971dfcbc9fd787cd0290795f79d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext 方法
此程序中設定給定執行緒的內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>參數  
 `threadID`  
 [in]這是要設定的內容執行緒的識別碼。  
  
 `contextSize`  
 [in] `context` 陣列的大小。  
  
 `context`  
 [in]描述執行緒的內容的位元組陣列。  
  
 內容指定在執行緒上執行的處理器架構。  
  
## <a name="remarks"></a>備註  
 偵錯工具應該呼叫這個方法，而不是 Win32`SetThreadContext`函式，因為執行緒實際上可能處於 「 被盜用 」 狀態中, 其內容已暫時變更。 只有在執行緒處於原生程式碼時，應該使用這個方法。 使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) managed 程式碼中的執行緒。 您應該永遠不需要修改期間的頻外 (OOB) 偵錯事件的執行緒內容。  
  
 傳遞的資料必須是目前的平台的內容結構。  
  
 如果不當使用，這個方法可能會損毀的執行階段。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
