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
ms.openlocfilehash: fffa61d8e406162251b0934a9846e5a813422798
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724581"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended 方法

取得值，這個值會指出指定的執行緒是否因偵錯工具停止此進程而暫止。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>參數  

 `threadID`  
 在有問題之執行緒的識別碼。  
  
 `pbSuspended`  
 擴展布林值的指標，如果指定的執行緒已暫止，則為， `true` 否則為 `pbSuspended` * `false` 。  
  
## <a name="remarks"></a>備註  

 當指定的執行緒因偵錯工具停止此進程而暫停時，指定執行緒的 Win32 暫止計數會遞增一。 如果偵錯工具使用者介面 (UI，) 可能會想要將這項資訊納入考慮，如果它顯示作業系統 (作業系統) 將執行緒的暫停計數加入使用者。  
  
 `IsOSSuspended`方法只有在未受管理的偵測內容中才有意義。 在 managed 錯錯期間，執行緒會以合作方式暫停，而不是由 OS 擱置。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
