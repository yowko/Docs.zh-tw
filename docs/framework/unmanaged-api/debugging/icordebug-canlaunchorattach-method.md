---
title: ICorDebug::CanLaunchOrAttach 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf0065f1ed12ad3a37819b0a15d734a2b51ff5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125602"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach 方法
會傳回 HRESULT，指出是否有可能在目前的電腦以及執行階段組態的內容中啟動新的處理序，或附加至指定的現有處理序。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwProcessId`  
 [in]現有的處理序的識別碼。  
  
 `win32DebuggingEnabled`  
 [in]傳入`true`如果您計劃使用 Win32 啟用偵錯，來啟動或附加啟用，否則，偵錯 Win32 傳遞`false`。  
  
## <a name="return-value"></a>傳回值  
 如果偵錯服務判斷啟動新的處理序，或附加至指定的處理序，為 S_OK 是可行的指定目前的電腦和執行階段組態的詳細資訊。 可能的 HRESULT 值為：  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>備註  
 這個方法僅供參考。 介面不會停止您無法啟動或附加至處理序，不論值傳回`CanLaunchOrAttach`。  
  
 若要啟動已啟用偵錯的 Win32 或附加啟用 Win32 偵錯，則會傳遞`true`針對`win32DebuggingEnabled`。 所傳回的 HRESULT`CanLaunchOrAttach`如果您使用此選項可能會不同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
