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
ms.openlocfilehash: 5b4052485a6d420eb83578d135ce51f8a918aab0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724516"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext 方法

設定這個進程中指定執行緒的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>參數  

 `threadID`  
 在要設定內容之執行緒的識別碼。  
  
 `contextSize`  
 [in] `context` 陣列的大小。  
  
 `context`  
 在描述執行緒內容的位元組陣列。  
  
 內容會指定執行緒執行所在的處理器架構。  
  
## <a name="remarks"></a>備註  

 偵錯工具應該呼叫這個方法，而不是 Win32 函式 `SetThreadContext` ，因為執行緒實際上可能會處於「被攔截」狀態，而其內容已暫時變更。 只有當執行緒在機器碼中時，才應該使用這個方法。 在 managed 程式碼中針對執行緒使用 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 。 在頻外 (OOB) debug 事件期間，您應該永遠不需要修改執行緒的內容。  
  
 傳遞的資料必須是目前平臺的內容結構。  
  
 如果使用不正確，此方法可能會損毀執行時間。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
