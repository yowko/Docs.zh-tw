---
title: "ICorDebugModule2::SetJMCStatus 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca4b53acc69d0a56b94526de0c3b16fd1abde077
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus 方法
設定的 Just My Code (JMC) 狀態的所有類別的所有方法和指定的值以外的這個 ICorDebugModule2`pTokens`陣列，它會設定為相反側的值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bIsJustMycode`  
 [in]設定為`true`程式碼是偵錯，否則如果設定為`false`。  
  
 `cTokens`  
 [in] `pTokens` 陣列的大小。  
  
 `pTokens`  
 [in]陣列`mdToken`值，其中每個方法將會有其 JMC 狀態設定為所指的是 ！`bIsJustMycode`。  
  
## <a name="remarks"></a>備註  
 每個方法中指定的 JMC 狀態`pTokens`陣列設相反`bIsJustMycode`值。 此模組中的其他所有方法的狀態設為`bIsJustMycode`值。  
  
 `SetJMCStatus`方法清除所有先前在此模組的 jmc 的方法設定。  
  
 `SetJMCStatus`方法會傳回 S_OK HRESULT，如果已成功設定所有函式。 它會傳回某些函式，如果 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT 標示`true`不是可偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
