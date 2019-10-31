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
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128762"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended 方法
取得值，指出指定的執行緒是否因偵錯工具停止這個進程而暫停。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>參數  
 `threadID`  
 在有問題的執行緒識別碼。  
  
 `pbSuspended`  
 脫銷布林值的指標，如果指定的執行緒已暫止，則為 `true`;否則，會 `false``pbSuspended`。  
  
## <a name="remarks"></a>備註  
 當指定的執行緒因偵錯工具停止這個進程而暫停時，指定的執行緒 Win32 暫停計數會遞增一。 如果偵錯工具使用者介面（UI）向使用者顯示執行緒的作業系統（OS）暫停計數，可能會想要將這項資訊列入考慮。  
  
 只有在未受管理的調試內容中，`IsOSSuspended` 方法才有意義。 在受管理的調試過程中，執行緒會以合作方式暫停，而不是由 OS 暫停。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
