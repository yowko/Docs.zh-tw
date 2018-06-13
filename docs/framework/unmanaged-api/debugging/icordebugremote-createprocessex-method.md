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
ms.openlocfilehash: 06bdc3605d981acad68a97901627f361da4061c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423315"
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
  
#### <a name="parameters"></a>參數  
 `pRemoteTarget`  
 [in]指標[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。 用來決定處理程序就會啟動所在的遠端電腦。  
  
 `lpApplicationName`  
 [in]以 null 終止的字串，指定要啟動的程序中執行之模組的指標。 呼叫處理序的安全性內容中執行模組。  
  
 `lpCommandLine`  
 [in]以 null 終止的字串，指定要啟動的程序中執行的命令列的指標。  
  
 `lpProcessAttributes`  
 [in]未使用的遠端偵錯。  
  
 `lpThreadAttributes`  
 [in]未使用的遠端偵錯。  
  
 `bInheritHandles`  
 [in]未使用的遠端偵錯。  
  
 `dwCreationFlags`  
 [in]未使用的遠端偵錯。  
  
 `lpEnvironment`  
 [in]新處理序的環境區塊的指標。  
  
 `lpCurrentDirectory`  
 [in]以 null 終止的字串，指定處理序的目前目錄的完整路徑的指標。 如果這個參數是 null，新處理序必須相同目前的磁碟機和目錄做為呼叫處理序。  
  
 `lpStartupInfo`  
 [in]未使用的遠端偵錯。  
  
 `lpProcessInformation`  
 [in]未使用的遠端偵錯。  
  
 `debuggingFlags`  
 [in]未使用的遠端偵錯。  
  
 `ppProcess`  
 [out]表示處理程序的 「 ICorDebugProcess 介面 」 物件的位址指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功啟動遠端電腦，並傳回 「 ICorDebugProcess 介面 」 上的處理序進行偵錯。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法啟動遠端電腦上的處理序，並傳回 「 ICorDebugProcess 介面 」，以供偵錯。  
  
## <a name="remarks"></a>備註  
 Silverlight 中不支援混合模式偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 4.5、 4、 3.5 SP1  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugRemote 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
