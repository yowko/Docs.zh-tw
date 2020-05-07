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
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859683"
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
 在如果您`true`打算在啟用 win32 偵測功能的情況下啟動，或在啟用 win32 偵測時附加，請傳入：否則，請`false`傳遞。  
  
## <a name="return-value"></a>傳回值  
 S_OK 偵錯工具是否可以判斷啟動新進程或附加至給定的進程，並提供目前電腦和執行時間設定的相關資訊。 可能的 HRESULT 值如下：  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>備註  
 這個方法是單純的資訊。 不論所傳回的值為何，介面都不會阻止您啟動或附加至進程`CanLaunchOrAttach`。  
  
 如果您打算在啟用 Win32 偵錯工具的情況下啟動或附加已啟用 Win32 `true`調試`win32DebuggingEnabled`程式，請傳遞 for。 如果您使用此`CanLaunchOrAttach`選項，所傳回的 HRESULT 可能會有所不同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](icordebug-interface.md)
