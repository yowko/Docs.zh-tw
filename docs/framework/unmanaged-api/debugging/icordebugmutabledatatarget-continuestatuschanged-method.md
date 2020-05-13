---
title: ICorDebugMutableDataTarget::ContinueStatusChanged 方法
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213305"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged 方法
變更指定執行緒上未處理之偵錯事件的接續狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>參數  
 `dwThreadId`  
 作業系統定義的執行緒識別項。  
  
 `continueStatus`  
 [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) 值，代表新要求的接續狀態。  
  
## <a name="remarks"></a>備註  
 當偵錯工具呼叫 ICorDebug 方法時，如果該方法處理目前偵錯事件的方式可能與正常處理方式不同，則會呼叫 `ContinueStatusChanged` 方法。 例如，如果有未處理的例外狀況，並且偵錯工具要求取消例外狀況的作業 (例如 [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) 或 `FuncEval`)，則會使用這個應用程式開發介面來要求取消例外狀況。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMutableDataTarget 介面](icordebugmutabledatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
