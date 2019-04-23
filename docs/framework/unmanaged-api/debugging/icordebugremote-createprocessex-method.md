---
title: ICorDebugRemote::CreateProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a38812803127857281f9766fa3ed551971ec0330
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093514"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx 方法
啟動處理序在偵錯工具在遠端電腦上。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a>參數  
 `pRemoteTarget`  
 [in]指標[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。 用來判斷遠端電腦將在其啟動處理程序。  
  
 `lpApplicationName`  
 [in]以 null 終止的字串，指定要啟動的程序執行模組的指標。 呼叫處理序的安全性內容中執行模組。  
  
 `lpCommandLine`  
 [in]以 null 終止的字串，指定要啟動的程序執行的命令列的指標。  
  
 `lpProcessAttributes`  
 [in]若未使用，可進行遠端偵錯。  
  
 `lpThreadAttributes`  
 [in]若未使用，可進行遠端偵錯。  
  
 `bInheritHandles`  
 [in]若未使用，可進行遠端偵錯。  
  
 `dwCreationFlags`  
 [in]若未使用，可進行遠端偵錯。  
  
 `lpEnvironment`  
 [in]新的處理序的環境區塊的指標。  
  
 `lpCurrentDirectory`  
 [in]以 null 終止的字串，指定處理程序的目前目錄的完整路徑的指標。 如果此參數為 null，新處理序會為呼叫處理序有相同的目前磁碟機和目錄。  
  
 `lpStartupInfo`  
 [in]若未使用，可進行遠端偵錯。  
  
 `lpProcessInformation`  
 [in]若未使用，可進行遠端偵錯。  
  
 `debuggingFlags`  
 [in]若未使用，可進行遠端偵錯。  
  
 `ppProcess`  
 [out]表示處理程序的 「 ICorDebugProcess 介面 」 物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功啟動遠端電腦並傳回 「 ICorDebugProcess 介面 」 上的處理序進行偵錯。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法啟動遠端電腦上的處理序，並傳回 「 ICorDebugProcess 介面 」 偵錯。  
  
## <a name="remarks"></a>備註  
 在 Silverlight 中不支援混合模式偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** 4.5，4，3.5 SP1  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRemote 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
