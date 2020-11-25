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
ms.openlocfilehash: 195c7e1e7c61fd6ac8a21226b52e3782d2f7e421
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723489"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach 方法

傳回 HRESULT，指出目前電腦和執行時間設定的內容中，是否可以啟動新的進程或附加至指定的現有進程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>參數  

 `dwProcessId`  
 在現有進程的識別碼。  
  
 `win32DebuggingEnabled`  
 在 `true` 如果您打算在啟用 win32 偵測的情況下啟動，或在已啟用 win32 調試的情況下進行附加，請傳入，否則傳遞 `false` 。  
  
## <a name="return-value"></a>傳回值  

 S_OK 如果偵錯工具會根據目前電腦和執行時間設定的相關資訊，判斷是否可以啟動新的進程或附加至指定的進程。 可能的 HRESULT 值為：  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>備註  

 這個方法純粹是資訊。 無論傳回的值為何，介面都不會阻止您啟動或附加至進程 `CanLaunchOrAttach` 。  
  
 如果您打算在啟用 Win32 偵錯工具的情況下啟動，或在啟用 Win32 偵錯工具的情況下進行附加，請傳遞 `true` `win32DebuggingEnabled` 。 如果您使用此選項，則所傳回的 HRESULT `CanLaunchOrAttach` 可能會不同。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
