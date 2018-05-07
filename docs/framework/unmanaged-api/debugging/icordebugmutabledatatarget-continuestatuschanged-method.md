---
title: ICorDebugMutableDataTarget::ContinueStatusChanged 方法
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb07c519743c41a7a31994e42d2fdc5220e5e2ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged 方法
變更指定執行緒上未處理之偵錯事件的接續狀態。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a>參數  
 `dwThreadId`  
 作業系統定義的執行緒識別項。  
  
 `continueStatus`  
 A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示新要求的接續狀態。  
  
## <a name="remarks"></a>備註  
 當偵錯工具呼叫 ICorDebug 方法時，如果該方法處理目前偵錯事件的方式可能與正常處理方式不同，則會呼叫 `ContinueStatusChanged` 方法。 例如，如果發生未處理的例外狀況，且偵錯工具要求會取消例外狀況的作業 (例如[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)或`FuncEval`)，此 API 用來要求的例外是已取消。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugMutableDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
