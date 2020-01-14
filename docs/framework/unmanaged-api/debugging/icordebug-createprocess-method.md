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
ms.openlocfilehash: a69fb861f7c2671a5c26245aa544ee99bcbdb56b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901003"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess 方法
在偵錯工具的控制項底下啟動進程和其主要執行緒。  
  
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
 在以 null 結束的字串指標，指定啟動的進程所要執行的模組。 模組會在呼叫進程的安全性內容中執行。  
  
 `lpCommandLine`  
 在以 null 結束的字串指標，指定啟動的進程所要執行的命令列。 應用程式名稱（例如，"SomeApp"）必須是第一個引數。  
  
 `lpProcessAttributes`  
 在Win32 `SECURITY_ATTRIBUTES` 結構的指標，指定進程的安全描述項。 如果 `lpProcessAttributes` 為 null，進程會取得預設的安全描述項。  
  
 `lpThreadAttributes`  
 在Win32 `SECURITY_ATTRIBUTES` 結構的指標，指定進程之主要執行緒的安全描述項。 如果 `lpThreadAttributes` 為 null，則執行緒會取得預設的安全描述項。  
  
 `bInheritHandles`  
 在設定為 `true`，表示已啟動的進程會繼承呼叫進程中的每個可繼承控制碼，或 `false` 表示不繼承控制碼。 繼承的控制碼與原始控制碼具有相同的值和存取權限。  
  
 `dwCreationFlags`  
 在[Win32 進程建立旗標](/windows/win32/procthread/process-creation-flags)的位元組合，可控制優先順序類別和已啟動進程的行為。  
  
 `lpEnvironment`  
 在新進程之環境區塊的指標。  
  
 `lpCurrentDirectory`  
 在以 null 結束的字串指標，指定進程目前目錄的完整路徑。 如果此參數為 null，新的進程將會具有與呼叫進程相同的目前磁片磁碟機和目錄。  
  
 `lpStartupInfo`  
 在Win32 `STARTUPINFOW` 結構的指標，指定啟動之進程的視窗站、桌面、標準控制碼，以及主視窗的外觀。  
  
 `lpProcessInformation`  
 在Win32 `PROCESS_INFORMATION` 結構的指標，指定要啟動之進程的識別資訊。  
  
 `debuggingFlags`  
 在指定偵錯工具選項的 CorDebugCreateProcessFlags 列舉值。  
  
 `ppProcess`  
 脫銷代表進程之 ICorDebugProcess 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 這個方法的參數與 Win32 `CreateProcess` 方法的參數相同。  
  
 若要啟用非受控混合模式的調試，請將&#124; `dwCreationFlags` 設定為 DEBUG_PROCESS DEBUG_ONLY_THIS_PROCESS。 如果您只想要使用受管理的調試，請勿設定這些旗標。  
  
 若偵錯工具和要進行調試的進程（附加的進程）共用單一主控台，而且使用 interop 偵錯工具，則附加的進程可能會保留主控台鎖定，並在 debug 事件停止。 然後偵錯工具會封鎖任何使用主控台的嘗試。 若要避免這個問題，請在 `dwCreationFlags` 參數中設定 CREATE_NEW_CONSOLE 旗標。  
  
 在 Win9x 和非 x86 平臺（例如 IA-64 型和以 AMD64 為基礎的平臺）上不支援 Interop 調試。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
