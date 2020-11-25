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
ms.openlocfilehash: cfa6df7a812559f05a4c57381a5007c9c90238e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709644"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus 方法

將這個 ICorDebugModule2 中所有類別的所有方法的 Just My Code (JMC) 狀態設定為指定的值，但陣列中的值除外 `pTokens` ，其會設定為相反值。  
  
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
 在 `true` 如果要偵錯工具代碼，請設定為，否則設定為 `false` 。  
  
 `cTokens`  
 [in] `pTokens` 陣列的大小。  
  
 `pTokens`  
 在值的陣列 `mdToken` ，每個值都會參考將其 JMC 狀態設為！的方法 `bIsJustMycode` 。  
  
## <a name="remarks"></a>備註  

 陣列中指定之每個方法的 JMC 狀態 `pTokens` 會設定為相對於 `bIsJustMycode` 該值的值。 此課程模組中所有其他方法的狀態都會設定為 `bIsJustMycode` 值。  
  
 `SetJMCStatus`此方法會清除此課程模組中所有先前的 JMC 設定。  
  
 `SetJMCStatus`如果已成功設定所有函數，方法會傳回 S_OK HRESULT。 如果某些標記的函式無法進行調試，它會傳回 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT `true` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
