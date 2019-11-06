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
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134275"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach 方法
傳回 HRESULT，指出目前的電腦和執行時間設定的內容中，是否可以啟動新進程或附加至指定的現有進程。  
  
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
 在傳入 `true` 如果您打算在啟用 Win32 偵測功能的情況下啟動，或附加至啟用 Win32 偵測，則為。否則，請傳遞 `false`。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果偵錯工具會判斷目前的電腦和執行時間設定的相關資訊，則可能會啟動新的進程或附加至給定的進程。 可能的 HRESULT 值如下：  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>備註  
 這個方法是單純的資訊。 無論 `CanLaunchOrAttach`傳回的值為何，介面都不會阻止您啟動或附加至進程。  
  
 如果您打算在啟用 Win32 偵錯工具的情況下啟動或附加已啟用 Win32 偵錯工具，請傳遞 `true` 以進行 `win32DebuggingEnabled`。 如果您使用此選項，`CanLaunchOrAttach` 所傳回的 HRESULT 可能會有所不同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
