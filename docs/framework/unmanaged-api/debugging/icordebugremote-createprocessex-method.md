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
ms.openlocfilehash: 37bf800f27754d1bf80aece962b7cbb85b1cbedc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712179"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx 方法

在偵錯工具下啟動遠端電腦上的處理常式。  
  
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
 在 [ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)的指標。 用來判斷將在其上啟動進程的遠端電腦。  
  
 `lpApplicationName`  
 在指標，指向以 null 終止的字串，這個字串會指定要由啟動的進程執行的模組。 模組會在呼叫進程的安全性內容中執行。  
  
 `lpCommandLine`  
 在指標，指向以 null 終止的字串，這個字串會指定啟動的進程所要執行的命令列。  
  
 `lpProcessAttributes`  
 在未使用進行遠端偵錯。  
  
 `lpThreadAttributes`  
 在未使用進行遠端偵錯。  
  
 `bInheritHandles`  
 在未使用進行遠端偵錯。  
  
 `dwCreationFlags`  
 在未使用進行遠端偵錯。  
  
 `lpEnvironment`  
 在新進程的環境區塊指標。  
  
 `lpCurrentDirectory`  
 在指標，指向以 null 終止的字串，這個字串會指定進程目前目錄的完整路徑。 如果此參數為 null，則新的進程會有與呼叫進程相同的目前磁片磁碟機和目錄。  
  
 `lpStartupInfo`  
 在未使用進行遠端偵錯。  
  
 `lpProcessInformation`  
 在未使用進行遠端偵錯。  
  
 `debuggingFlags`  
 在未使用進行遠端偵錯。  
  
 `ppProcess`  
 擴展代表進程之「ICorDebugProcess 介面」物件位址的指標。  
  
## <a name="return-value"></a>傳回值  

 S_OK  
 已成功啟動遠端電腦上的處理常式，並傳回「ICorDebugProcess 介面」以進行偵錯工具。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法在遠端電腦上啟動處理常式，並傳回「ICorDebugProcess 介面」以進行偵錯工具。  
  
## <a name="remarks"></a>備註  

 Silverlight 不支援混合模式的偵錯工具。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRemote 介面](icordebugremote-interface.md)
- [ICorDebug 介面](icordebug-interface.md)

- [偵錯介面](debugging-interfaces.md)
