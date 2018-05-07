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
ms.openlocfilehash: 044f94a567dc4bc2b169ba2a5f2a5d7b4f98e516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess 方法
啟動處理序與它所控制的偵錯工具的主要執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `lpApplicationName`  
 [in]以 null 終止的字串，指定要啟動的程序中執行之模組的指標。 呼叫處理序的安全性內容中執行模組。  
  
 `lpCommandLine`  
 [in]以 null 終止的字串，指定要啟動的程序中執行的命令列的指標。 應用程式名稱 (例如，"SomeApp.exe") 必須是第一個引數。  
  
 `lpProcessAttributes`  
 [in]對 win32 指標`SECURITY_ATTRIBUTES`結構，指定處理程序的安全性描述元。 如果`lpProcessAttributes`是 null，此程序取得預設安全性描述元。  
  
 `lpThreadAttributes`  
 [in]對 win32 指標`SECURITY_ATTRIBUTES`結構，指定處理程序的主執行緒的安全性描述元。 如果`lpThreadAttributes`是 null，執行緒會取得預設安全性描述元。  
  
 `bInheritHandles`  
 [in]設定為`true`表示啟動處理程序會繼承呼叫處理序中的每個繼承控制代碼或`false`表示不會繼承控制代碼。 繼承的控制代碼具有相同的值與存取權限，原始的控制代碼的形式。  
  
 `dwCreationFlags`  
 [in]位元組合[Win32 處理序建立旗標](http://go.microsoft.com/fwlink/?linkid=69981)所控制的優先權等級和啟動處理序的行為。  
  
 `lpEnvironment`  
 [in]新處理序的環境區塊的指標。  
  
 `lpCurrentDirectory`  
 [in]以 null 終止的字串，指定處理序的目前目錄的完整路徑的指標。 如果這個參數是 null，新處理序必須相同目前的磁碟機和目錄做為呼叫處理序。  
  
 `lpStartupInfo`  
 [in]對 win32 指標`STARTUPINFOW`結構，指定視窗工作站、 桌面、 標準的控制代碼和啟動處理序主視窗的外觀。  
  
 `lpProcessInformation`  
 [in]對 win32 指標`PROCESS_INFORMATION`結構，指定要啟動之處理序識別資訊。  
  
 `debuggingFlags`  
 [in]CorDebugCreateProcessFlags 列舉，指定偵錯選項的值。  
  
 `ppProcess`  
 [out]ICorDebugProcess 物件代表處理程序的位址指標。  
  
## <a name="remarks"></a>備註  
 這個方法的參數都是一樣的 Win32`CreateProcess`方法。  
  
 若要啟用未受管理的混合模式偵錯，設定`dwCreationFlags`至 DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS。 如果您想要使用只有 managed 偵錯時，未設定這些旗標。  
  
 如果偵錯工具和程序要偵錯 （附加的處理序） 共用單一主控台中，並使用 interop 偵錯時，它是否可以保留主控台鎖定，而且在偵錯事件停止附加的處理序。 偵錯工具就會封鎖任何嘗試使用主控台。 若要避免這個問題，請設定 CREATE_NEW_CONSOLE 旗標`dwCreationFlags`參數。  
  
 在 Win9x 和非 x86 的平台，例如 IA 64 型和 amd64 平台上不支援 interop 偵錯。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
