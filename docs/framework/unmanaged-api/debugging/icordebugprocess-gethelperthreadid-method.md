---
title: "ICorDebugProcess::GetHelperThreadID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03e801cb58b8f5c3f658085fcee4288278e545c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID 方法
取得偵錯工具的內部協助程式執行緒的作業系統 (OS) 執行緒識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThreadID`  
 [out]指向 OS 執行緒偵錯工具的內部協助程式執行緒的 ID。  
  
## <a name="remarks"></a>備註  
 Managed 和 unmanaged 偵錯期間，是以確保具有指定識別碼的執行緒保持執行，如果叫用中斷點放在偵錯工具偵錯工具的責任。 偵錯工具可能也想要隱藏使用者從這個執行緒。 如果沒有協助程式執行緒存在於處理程序，`GetHelperThreadID`方法會傳回零 *`pThreadID`。  
  
 因為它會隨著時間變更，無法快取，在協助程式執行緒的執行緒 ID。 您必須重新查詢在每個停止事件的執行緒 ID。  
  
 偵錯工具 helper 執行緒的執行緒 ID 將會是正確的每個 unmanaged [icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)事件，如此可讓偵錯工具若要判斷其協助程式執行緒的執行緒 ID 和隱藏使用者。 被視為期間未受管理的協助程式執行緒的執行緒`ICorDebugManagedCallback::CreateThread`事件永遠不會執行 managed 的使用者程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl。 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
