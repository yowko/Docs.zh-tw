---
title: ICorDebugThread::GetCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762476"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException 方法
ICorDebugValue 物件，表示目前正在 managed 程式碼所擲回例外狀況取得的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppExceptionObject`  
 [out]位址指標`ICorDebugValue`物件，表示目前所所擲回的例外狀況的 managed 程式碼。  
  
## <a name="remarks"></a>備註  
 例外狀況物件會存在直到結束擲出例外狀況的時間從`catch`區塊。 函式評估，這會由 ICorDebugEval 方法執行，將會清除例外狀況物件上設定，然後將其還原完成。  
  
 （例如，如果在篩選中，或在函式評估，則會擲回例外狀況），可以巢狀例外狀況，因此可能會有單一執行緒上的多個未處理例外狀況。 `GetCurrentException` 傳回最新的例外狀況。  
  
 例外狀況物件和型別可能會變更整個生命週期的例外狀況。 比方說，會擲回例外狀況型別 x 的之後，common language runtime (CLR) 可能會用盡記憶體，並將它升級到記憶體不足例外狀況。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
