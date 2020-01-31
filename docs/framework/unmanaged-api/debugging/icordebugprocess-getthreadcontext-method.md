---
title: ICorDebugProcess::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 41c5116d23655730f3586dc656aa69c8ae817b6c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792616"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext 方法
取得這個進程中指定執行緒的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>參數  
 `threadID`  
 在要為其取得內容的執行緒識別碼。  
  
 `contextSize`  
 [in] `context` 陣列的大小。  
  
 `context`  
 [in、out]描述執行緒內容的位元組陣列。  
  
 內容會指定執行緒在其上執行的處理器架構。  
  
## <a name="remarks"></a>備註  
 偵錯工具應該呼叫這個方法，而不是 Win32 `GetThreadContext` 方法，因為執行緒可能會處於「遭劫持」狀態，而其內容已暫時變更。 只有線上程是機器碼時，才應該使用這個方法。 針對 managed 程式碼中的執行緒使用[ICorDebugRegisterSet](icordebugregisterset-interface.md) 。  
  
 傳回的資料是目前平臺的內容結構。 如同 Win32 `GetThreadContext` 方法，呼叫端應該先初始化 `context` 參數，然後再呼叫這個方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
