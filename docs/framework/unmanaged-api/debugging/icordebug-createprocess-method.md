---
title: ICorDebug::CreateProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d6220270634dd8e2d15787d717020b8f6f86bb9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738324"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess 方法
啟動處理程序和它所控制的偵錯工具的主要執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a>參數  
 `lpApplicationName`  
 [in]以 null 終止的字串，指定要啟動的程序執行模組的指標。 呼叫處理序的安全性內容中執行模組。  
  
 `lpCommandLine`  
 [in]以 null 終止的字串，指定要啟動的程序執行的命令列的指標。 應用程式名稱 (例如，"SomeApp.exe") 必須是第一個引數。  
  
 `lpProcessAttributes`  
 [in]Win32 指標`SECURITY_ATTRIBUTES`結構，指定處理程序的安全性描述元。 如果`lpProcessAttributes`是 null，此程序取得的預設安全性描述元。  
  
 `lpThreadAttributes`  
 [in]Win32 指標`SECURITY_ATTRIBUTES`結構，指定處理程序的主執行緒的安全性描述元。 如果`lpThreadAttributes`是 null，執行緒會取得預設安全性描述元。  
  
 `bInheritHandles`  
 [in]設定為`true`表示啟動的程序，會繼承呼叫處理序中的每個可繼承控制代碼或`false`表示不會繼承控制代碼。 繼承的控制代碼具有相同的值與存取權限，原始的控制代碼的形式。  
  
 `dwCreationFlags`  
 [in]位元組合[Win32 處理序建立旗標](https://go.microsoft.com/fwlink/?linkid=69981)，以控制的優先權等級以及啟動的程序的行為。  
  
 `lpEnvironment`  
 [in]新的處理序的環境區塊的指標。  
  
 `lpCurrentDirectory`  
 [in]以 null 終止的字串，指定處理程序的目前目錄的完整路徑的指標。 如果此參數為 null，新處理序會為呼叫處理序有相同的目前磁碟機和目錄。  
  
 `lpStartupInfo`  
 [in]Win32 指標`STARTUPINFOW`結構，指定視窗工作站、 桌面、 標準的控制代碼和啟動的程序的主視窗的外觀。  
  
 `lpProcessInformation`  
 [in]Win32 指標`PROCESS_INFORMATION`結構，指定要啟動的程序的識別資訊。  
  
 `debuggingFlags`  
 [in]CorDebugCreateProcessFlags 列舉，指定偵錯的選項值。  
  
 `ppProcess`  
 [out]ICorDebugProcess 物件代表處理程序的位址指標。  
  
## <a name="remarks"></a>備註  
 這個方法的參數是一樣的 Win32`CreateProcess`方法。  
  
 若要啟用非受控的混合模式偵錯，設定`dwCreationFlags`DEBUG_PROCESS 到&#124;DEBUG_ONLY_THIS_PROCESS。 如果您想要使用只有 managed 偵錯時，未設定這些旗標。  
  
 如果要偵錯工具和程序進行偵錯 （附加的處理序） 共用單一主控台中，如果使用 interop 偵錯時，您也可以鎖定主控台，並停止偵錯事件在附加的處理序。 偵錯工具就會封鎖任何嘗試使用主控台。 若要避免這個問題，請在中設定 CREATE_NEW_CONSOLE 旗標`dwCreationFlags`參數。  
  
 不支援 Win9x 和非 x86 的平台，例如 IA-64 架構和 amd64 平台的 interop 偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
