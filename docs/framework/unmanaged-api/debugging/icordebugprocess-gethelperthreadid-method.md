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
ms.openlocfilehash: 77cc658e28c7a69d8c4aeeed2f3e7ea40f0d2af6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724568"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID 方法

取得作業系統 (作業系統) 偵錯工具內部 helper 執行緒的執行緒識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>參數  

 `pThreadID`  
 擴展偵錯工具之內部 helper 執行緒的 OS 執行緒識別碼指標。  
  
## <a name="remarks"></a>備註  

 在受控和非受控的偵錯工具期間，偵錯工具必須負責確保具有指定識別碼的執行緒在叫用偵錯工具所放置的中斷點時仍繼續執行。 偵錯工具也可能會想要從使用者隱藏這個執行緒。 如果進程中沒有 helper 執行緒存在， `GetHelperThreadID` 方法會在 * 中傳回零 `pThreadID` 。  
  
 您無法快取 helper 執行緒的執行緒識別碼，因為它可能會隨著時間而變更。 您必須在每次停止事件時重新查詢執行緒識別碼。  
  
 偵錯工具 helper 執行緒的執行緒識別碼在每個非受控 [ICorDebugManagedCallback：： CreateThread](icordebugmanagedcallback-createthread-method.md) 事件上都是正確的，因此可讓偵錯工具判斷其 helper 執行緒的執行緒識別碼，並將其從使用者中隱藏。 在非受控事件期間識別為 helper 執行緒的執行緒 `ICorDebugManagedCallback::CreateThread` 永遠不會執行受管理的使用者程式碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl。 Cordebug.h。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
