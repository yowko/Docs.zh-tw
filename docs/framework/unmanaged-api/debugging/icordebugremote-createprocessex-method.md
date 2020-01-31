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
ms.openlocfilehash: cfec84483d387630623f77c176c668171303dd0f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791982"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx 方法
在偵錯工具下的遠端電腦上啟動進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在[ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)的指標。 用來判斷將在其上啟動進程的遠端電腦。  
  
 `lpApplicationName`  
 在以 null 結束的字串指標，指定啟動的進程所要執行的模組。 模組會在呼叫進程的安全性內容中執行。  
  
 `lpCommandLine`  
 在以 null 結束的字串指標，指定啟動的進程所要執行的命令列。  
  
 `lpProcessAttributes`  
 在未使用遠端偵錯程式。  
  
 `lpThreadAttributes`  
 在未使用遠端偵錯程式。  
  
 `bInheritHandles`  
 在未使用遠端偵錯程式。  
  
 `dwCreationFlags`  
 在未使用遠端偵錯程式。  
  
 `lpEnvironment`  
 在新進程之環境區塊的指標。  
  
 `lpCurrentDirectory`  
 在以 null 結束的字串指標，指定進程目前目錄的完整路徑。 如果此參數為 null，新的進程將會具有與呼叫進程相同的目前磁片磁碟機和目錄。  
  
 `lpStartupInfo`  
 在未使用遠端偵錯程式。  
  
 `lpProcessInformation`  
 在未使用遠端偵錯程式。  
  
 `debuggingFlags`  
 在未使用遠端偵錯程式。  
  
 `ppProcess`  
 脫銷代表進程之 "ICorDebugProcess Interface" 物件位址的指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功啟動遠端電腦上的進程，並傳回「ICorDebugProcess 介面」以進行偵錯工具。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法在遠端電腦上啟動進程，並傳回「ICorDebugProcess 介面」以進行偵錯工具。  
  
## <a name="remarks"></a>備註  
 Silverlight 中不支援混合模式的調試。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRemote 介面](icordebugremote-interface.md)
- [ICorDebug 介面](icordebug-interface.md)

- [偵錯介面](debugging-interfaces.md)
