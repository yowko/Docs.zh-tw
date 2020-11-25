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
ms.openlocfilehash: aeb39782c4c0624501a0e2a71960f5d16ab3c03e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723476"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess 方法

在偵錯工具的控制下啟動進程和其主要執行緒。  
  
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
 在指標，指向以 null 終止的字串，這個字串會指定要由啟動的進程執行的模組。 模組會在呼叫進程的安全性內容中執行。  
  
 `lpCommandLine`  
 在指標，指向以 null 終止的字串，這個字串會指定啟動的進程所要執行的命令列。 應用程式名稱 (例如 "SomeApp.exe" ) 必須是第一個引數。  
  
 `lpProcessAttributes`  
 在Win32 `SECURITY_ATTRIBUTES` 結構的指標，指定進程的安全描述項。 如果 `lpProcessAttributes` 是 null，進程會取得預設安全描述項。  
  
 `lpThreadAttributes`  
 在Win32 `SECURITY_ATTRIBUTES` 結構的指標，指定進程主要執行緒的安全描述項。 如果 `lpThreadAttributes` 是 null，則執行緒會取得預設安全描述項。  
  
 `bInheritHandles`  
 在設定為， `true` 表示已啟動的進程會繼承呼叫進程中的每個可繼承控制碼，或 `false` 表示不會繼承控制碼。 繼承的控制碼具有與原始控制碼相同的值和存取權限。  
  
 `dwCreationFlags`  
 在 [Win32 進程建立旗標](/windows/win32/procthread/process-creation-flags) 的位元組合，可控制優先權類別和已啟動進程的行為。  
  
 `lpEnvironment`  
 在新進程的環境區塊指標。  
  
 `lpCurrentDirectory`  
 在指標，指向以 null 終止的字串，這個字串會指定進程目前目錄的完整路徑。 如果此參數為 null，則新的進程會有與呼叫進程相同的目前磁片磁碟機和目錄。  
  
 `lpStartupInfo`  
 在Win32 `STARTUPINFOW` 結構的指標，指定所啟動進程的視窗站、桌面、標準控點和主視窗外觀。  
  
 `lpProcessInformation`  
 在Win32 `PROCESS_INFORMATION` 結構的指標，指定要啟動之進程的識別資訊。  
  
 `debuggingFlags`  
 在CorDebugCreateProcessFlags 列舉的值，這個值會指定偵錯工具選項。  
  
 `ppProcess`  
 擴展代表進程之 ICorDebugProcess 物件位址的指標。  
  
## <a name="remarks"></a>備註  

 這個方法的參數與 Win32 方法的參數相同 `CreateProcess` 。  
  
 若要啟用非受控混合模式的調試，請將設定 `dwCreationFlags` 為 DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS。 如果您只想要使用 managed 調試，請勿設定這些旗標。  
  
 如果偵錯工具和進程 (附加的進程) 共用單一主控台，而且使用 interop 偵錯工具，則附加的進程可能會保存主控台鎖定，並在偵錯工具中停止。 偵錯工具接著會封鎖任何使用主控台的嘗試。 若要避免這個問題，請在參數中設定 CREATE_NEW_CONSOLE 旗標 `dwCreationFlags` 。  
  
 在 Win9x 和非 x86 平臺（例如 IA-64 和 AMD64 平臺）上，不支援 Interop 偵錯工具。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
