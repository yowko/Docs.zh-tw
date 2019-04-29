---
title: ICorDebugProcess::IsOSSuspended 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775559"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended 方法
取得值，指出指定的執行緒是否已暫停偵錯工具停止此程序的結果。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>參數  
 `threadID`  
 [in]有問題的執行緒識別碼。  
  
 `pbSuspended`  
 [out]布林值的指標`true`如果指定的執行緒已經暫止，否則為 *`pbSuspended`是`false`。  
  
## <a name="remarks"></a>備註  
 指定的執行緒的 Win32 時指定的執行緒已暫停偵錯工具停止此程序的結果，暫停計數會遞增 1。 偵錯工具使用者介面 (UI) 可能想要讓這項資訊列入考量，如果它會顯示作業系統 (OS) 暫止的執行緒給使用者的計數。  
  
 `IsOSSuspended`方法有意義的非受控偵錯內容中。 Managed 偵錯期間，執行緒是以合作方式暫止而不是不是 OS 暫止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
