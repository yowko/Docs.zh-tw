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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764112"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus 方法
設定 Just My Code (JMC) 狀態的所有類別的所有方法中指定的值，不屬於此 ICorDebugModule2`pTokens`陣列，它會設定為相反值。  
  
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
 [in]設定為`true`程式碼是偵錯，否則如果設定為`false`。  
  
 `cTokens`  
 [in] `pTokens` 陣列的大小。  
  
 `pTokens`  
 [in]陣列`mdToken`值，其中每個參考的方法，會有其 JMC 狀態設為 ！`bIsJustMycode`。  
  
## <a name="remarks"></a>備註  
 每個方法中指定的 JMC 狀態`pTokens`陣列設為相對於`bIsJustMycode`值。 此模組中的所有其他方法的狀態設定為 `bIsJustMycode`值。  
  
 `SetJMCStatus`方法會清除所有先前的 JMC 設定值，這個模組中。  
  
 `SetJMCStatus`方法會傳回 S_OK HRESULT，如果已成功設定所有函式。 它會傳回某些函式，如果 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT 會標示`true`不是可偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
