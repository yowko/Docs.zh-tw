---
title: 適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77164f9d8a1641ba37fa504d09d77ec6aecc3db5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502373"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式
接受從傳回的常見 language runtime (CLR) 版本字串[CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)，並傳回對應的偵錯工具介面 (通常[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md))。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>參數  
 `szDebuggeeVersion`  
 [in]中的 目標偵錯項目，傳回的 CLR 版本字串[CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)。  
  
 `ppCordb`  
 [out] COM 物件 (`IUnknown`) 指標的指標。 這個物件會轉換成[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件再傳回。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 `ppCordb` 參考有效的物件，可實作[ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面。  
  
 E_INVALIDARG  
 `szDebuggeeVersion` 或 `ppCordb` 為 null。  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 找不到 CLR 偵錯所需的元件。 這表示在目標 CoreCLR.dll 所在的相同目錄中找不到 mscordbi.dll 或 mscordaccore.dll。  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 mscordbi.dll 或 mscordaccore.dll 的版本與目標 CoreCLR.dll 的版本不同。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法傳回[ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)。  
  
## <a name="remarks"></a>備註  
 傳回的介面提供了附加至目標處理序中的 CLR，以及對 CLR 正在執行之 Managed 程式碼進行偵錯的功能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** dbgshim.h  
  
 **程式庫：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
