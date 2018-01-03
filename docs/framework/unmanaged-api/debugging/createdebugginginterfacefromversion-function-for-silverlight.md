---
title: "適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c38171c5887bb207b3692e9fa92aa2be2bc72a27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式
接受 common language runtime (CLR) 版本字串所傳回的[CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)，並傳回對應的偵錯工具介面 (一般而言， [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md))。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szDebuggeeVersion`  
 [in]傳回目標偵錯項目，在 CLR 的版本字串[CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)。  
  
 `ppCordb`  
 [out] COM 物件 (`IUnknown`) 指標的指標。 這個物件會轉換成[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件傳回之前。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 `ppCordb`參考實作的有效物件[ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面。  
  
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
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** dbgshim.h  
  
 **程式庫：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
