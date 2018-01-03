---
title: "ICorDebug::CanLaunchOrAttach 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CanLaunchOrAttach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62ebdb178ef7aaa16bcc163e42662e1d69f1f6f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach 方法
會傳回 HRESULT，指出是否可以啟動新的處理序或附加至指定的現有處理序內目前的電腦和執行階段組態的內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwProcessId`  
 [in]現有的處理序的識別碼。  
  
 `win32DebuggingEnabled`  
 [in]傳入`true`您計劃啟動，發生 Win32 啟用偵錯，或附加啟用，否則，偵錯 Win32 傳遞`false`。  
  
## <a name="return-value"></a>傳回值  
 如果偵錯服務判斷可啟動新的處理序或附加至指定的處理序，為 S_OK，會假設目前的電腦和執行階段組態的相關資訊。 可能的 HRESULT 值為：  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>備註  
 這個方法僅供參考。 介面不會停止您啟動或附加至處理序，不論值傳回的`CanLaunchOrAttach`。  
  
 如果您打算啟動啟用偵錯的 Win32 或附加啟用偵錯 Win32，請傳遞`true`如`win32DebuggingEnabled`。 所傳回的 HRESULT`CanLaunchOrAttach`可能會與不同，如果您使用此選項。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
