---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a>ICorDebugModule Interface1
表示 common language runtime (CLR) 模組，可執行檔或動態連結程式庫 (DLL)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|未實作。|  
|[EnableClassLoadCallbacks 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|決定是否[icordebugmanagedcallback:: Loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)和[icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)針對此模組會呼叫的回呼。|  
|[EnableJITDebugging 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|決定是否在 just-in-time (JIT) 編譯器會保留在這個模組中方法的偵錯資訊。|  
|[GetAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|取得針對此模組包含組件。|  
|[GetBaseAddress 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|取得模組的基底位址。|  
|[GetClassFromToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|取得 ICorDebugClass 從中繼資料。|  
|[GetEditAndContinueSnapshot 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|已取代。|  
|[GetFunctionFromRVA 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|未實作。|  
|[GetFunctionFromToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|取得指定中繼資料語彙基元的函式。|  
|[GetGlobalVariableValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|取得指定之全域變數的值物件。|  
|[GetMetaDataInterface 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|取得可以用來檢查模組的中繼資料的中繼資料介面指標。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|取得模組的檔案名稱。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|取得此模組包含處理序。|  
|[GetSize 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|取得模組的大小，以位元組為單位。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|取得表格項目，此模組中的語彙基元。|  
|[IsDynamic 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|指出是否為動態模組。|  
|[IsInMemory 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|指出是否此模組只存在於記憶體。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
