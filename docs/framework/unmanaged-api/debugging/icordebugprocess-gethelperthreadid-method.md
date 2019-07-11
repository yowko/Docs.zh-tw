---
title: ICorDebugProcess::GetHelperThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad62b267eb0c49ff8fbefeb45b523c21edc705fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766050"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID 方法
取得偵錯工具的內部協助程式執行緒的作業系統 (OS) 執行緒識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>參數  
 `pThreadID`  
 [out]指標，OS 執行緒偵錯工具的內部協助程式執行緒的 ID。  
  
## <a name="remarks"></a>備註  
 Managed 和 unmanaged 偵錯期間，是偵錯工具的責任，以確保具有指定識別碼的執行緒保持執行，如果配接器放在偵錯工具的中斷點。 偵錯工具，也可能想要隱藏此執行緒使用者。 如果沒有任何協助程式執行緒，存在於處理程序`GetHelperThreadID`方法會傳回零 *`pThreadID`。  
  
 因為它可能會隨著時間改變，您無法快取的協助程式 」 執行緒的執行緒識別碼。 您必須重新查詢在每個停止事件的執行緒識別碼。  
  
 偵錯工具的協助程式執行緒的執行緒識別碼將會是正確的每個非受控[icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)事件，因此讓偵錯工具，判斷其協助程式執行緒的執行緒識別碼，並向使用者隱藏它。 被視為期間未受管理的協助程式執行緒的執行緒`ICorDebugManagedCallback::CreateThread`事件永遠不會執行 managed 的使用者程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl。 CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
