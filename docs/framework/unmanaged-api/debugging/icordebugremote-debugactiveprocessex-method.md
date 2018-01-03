---
title: "ICorDebugRemote::DebugActiveProcessEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.DebugActiveProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09bc98b477231eb1466300451585f4569aff222c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx 方法
啟動處理序在偵錯工具在遠端電腦上。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRemoteTarget`  
 [in]指標[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。 這個參數用來判斷處理程序執行所在的電腦。  
  
 `id`  
 [in]是要附加偵錯工具處理序的識別碼。  
  
 `win32Attach`  
 [in]`true`如果偵錯工具時應做為 Win32 偵錯工具處理序的行為及分派 unmanaged 的回呼中; 否則`false`。  
  
 `ppProcess`  
 [out]表示要附加偵錯工具的程序的"ICorDebugProcess 」 物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功連接至遠端電腦上的處理序。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法附加至遠端電腦上的處理序。  
  
## <a name="remarks"></a>備註  
 Silverlight 中不支援混合模式偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 4.5、 4、 3.5 SP1  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugRemote 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
