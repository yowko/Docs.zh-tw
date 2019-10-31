---
title: ICorDebugModule2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129476"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus 方法
將此 ICorDebugModule2 中所有類別的所有方法的 Just My Code （JMC）狀態設定為指定的值，但在 `pTokens` 陣列中，它會設定為相反的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `bIsJustMycode`  
 在如果要偵錯工具代碼，請設定為 `true`;否則，請將設定為 `false`。  
  
 `cTokens`  
 [in] `pTokens` 陣列的大小。  
  
 `pTokens`  
 在`mdToken` 值的陣列，其中每一個都參考將其 JMC 狀態設定為的方法！`bIsJustMycode`。  
  
## <a name="remarks"></a>備註  
 `pTokens` 陣列中指定之每個方法的 JMC 狀態都會設定為與 `bIsJustMycode` 值相反的。 此模組中所有其他方法的狀態會設定為 `bIsJustMycode` 值。  
  
 `SetJMCStatus` 方法會清除此課程模組中所有先前的 JMC 設定。  
  
 如果已成功設定所有函數，`SetJMCStatus` 方法會傳回 S_OK HRESULT。 如果某些已標記 `true` 的函式無法進行調試，它會傳回 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
