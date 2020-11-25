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
ms.openlocfilehash: 3be689e5c1474bcbfbca72a14a298762dc2e7a90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724542"
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
 在要取得其內容之執行緒的識別碼。  
  
 `contextSize`  
 [in] `context` 陣列的大小。  
  
 `context`  
 [in，out]描述執行緒內容的位元組陣列。  
  
 內容會指定執行緒執行所在的處理器架構。  
  
## <a name="remarks"></a>備註  

 偵錯工具應該呼叫這個方法，而不是 Win32 `GetThreadContext` 方法，因為執行緒實際上可能會處於「被攔截」狀態，而其內容已暫時變更。 只有當執行緒在機器碼中時，才應該使用這個方法。 在 managed 程式碼中針對執行緒使用 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 。  
  
 傳回的資料是目前平臺的內容結構。 就像使用 Win32 `GetThreadContext` 方法一樣，呼叫端應該先初始化 `context` 參數，然後再呼叫這個方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
