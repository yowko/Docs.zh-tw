---
title: ICorDebugManagedCallback::UpdateModuleSymbols 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
ms.openlocfilehash: 9ee6f43c94b8ff2e765d2a0dde0697c4c895a94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212369"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols 方法
通知偵錯工具，通用語言執行時間模組的符號已經變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，代表包含已變更符號之模組的應用程式域。  
  
 `pModule`  
 在ICorDebugModule 物件的指標，表示符號已變更的模組。  
  
 `pSymbolStream`  
 在Win32 COM 物件的指標 `IStream` ，其中包含修改過的符號。  
  
## <a name="remarks"></a>備註  
 這個方法可讓您藉由呼叫[ISymUnmanagedReader：： UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)或[ISymUnmanagedReader：： ReplaceSymbolStore](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md)，來更新偵錯工具的模組符號的觀點。  
  
 針對相同的模組，此回呼可能會發生多次。  
  
 偵錯工具應該嘗試系結未系結的來源層級中斷點。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
