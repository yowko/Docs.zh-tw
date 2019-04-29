---
title: ICorDebugController::Continue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eacffe5769bc77ab626f6adbc99db1137da565f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749666"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue 方法
之後繼續執行的受管理的執行緒呼叫[Stop 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a>參數  
 `fIsOutOfBand`  
 [in]設定為`true`如果超出訊號範圍的事件，從繼續執行，否則設定為`false`。  
  
## <a name="remarks"></a>備註  
 `Continue` 若要在呼叫之後繼續進行的程序`ICorDebugController::Stop`方法。  
  
 在執行混合模式偵錯時，請勿呼叫`Continue`win32 事件執行緒除非您要繼續從超出訊號範圍的事件。  
  
 *頻內事件*managed 的事件或一般的非受控的事件期間偵錯工具支援互動的程序的受管理狀態。 在此情況下，偵錯工具收到[icordebugunmanagedcallback:: Debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)具有回呼其`fOutOfBand`參數設定為`false`。  
  
 *頻外事件*是互動的程序的受管理狀態的期間不可能因為事件而停止處理程序時未受管理的事件。 在此情況下，偵錯工具收到`ICorDebugUnmanagedCallback::DebugEvent`具有回呼其`fOutOfBand`參數設為`true`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
