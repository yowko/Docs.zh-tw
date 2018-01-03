---
title: "ICorDebugController::Continue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue 方法
之後繼續執行的 managed 執行緒的呼叫[停止方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fIsOutOfBand`  
 [in]設定為`true`繼續從超出訊號範圍的事件; 否則設為`false`。  
  
## <a name="remarks"></a>備註  
 `Continue`若要在呼叫之後繼續進行程序`ICorDebugController::Stop`方法。  
  
 在執行混合模式偵錯時，請勿呼叫`Continue`上 Win32 事件執行緒除非您要繼續從超出訊號範圍的事件。  
  
 *頻外事件*managed 的事件或在偵錯工具支援與受管理狀態的處理程序互動的一般 unmanaged 的事件。 在此情況下，偵錯工具會接收[icordebugunmanagedcallback:: Debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)回呼其`fOutOfBand`參數設定為`false`。  
  
 *的頻外事件*是 unmanaged 期間互動的程序的受管理狀態時，不可能因為發生事件停止處理序的事件。 在此情況下，偵錯工具會接收`ICorDebugUnmanagedCallback::DebugEvent`回呼其`fOutOfBand`參數設定為`true`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 
