---
title: "ICorDebugProcess::GetThreadContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e45d101db946747463ba4200bc5dd3b95d21391
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext 方法
取得這個處理程序中指定之執行緒的內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>參數  
 `threadID`  
 [in]要擷取的內容執行緒的識別碼。  
  
 `contextSize`  
 [in] `context` 陣列的大小。  
  
 `context`  
 [in、 out]描述執行緒的內容的位元組陣列。  
  
 內容指定在執行緒上執行的處理器架構。  
  
## <a name="remarks"></a>備註  
 偵錯工具應該呼叫這個方法，而不是 Win32`GetThreadContext`方法，因為執行緒實際上可能處於 「 被盜用 」 狀態中, 其內容已暫時變更。 只有在執行緒處於原生程式碼時，應該使用這個方法。 使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) managed 程式碼中的執行緒。  
  
 傳回的資料是目前的平台的內容結構。 如同 Win32`GetThreadContext`方法，呼叫端應該初始化`context`之前呼叫這個方法的參數。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
