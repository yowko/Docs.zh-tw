---
title: ICorDebugModule 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 86e17b48bc491c45f8b46be23ab626dc1f2a6962
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709839"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule 介面

代表 common language runtime (CLR) 模組，這是可執行檔或動態連結程式庫 (DLL) 。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](icordebugmodule-createbreakpoint-method.md)|未實作。|  
|[EnableClassLoadCallbacks 方法](icordebugmodule-enableclassloadcallbacks-method.md)|判斷是否針對此模組呼叫 [ICorDebugManagedCallback：： LoadClass](icordebugmanagedcallback-loadclass-method.md) 和 [ICorDebugManagedCallback：： UnloadClass](icordebugmanagedcallback-unloadclass-method.md) 回呼。|  
|[EnableJITDebugging 方法](icordebugmodule-enablejitdebugging-method.md)|判斷及時 (JIT) 編譯器是否保留此模組內方法的偵錯工具資訊。|  
|[GetAssembly 方法](icordebugmodule-getassembly-method.md)|取得此模組的包含元件。|  
|[GetBaseAddress 方法](icordebugmodule-getbaseaddress-method.md)|取得模組的基底位址。|  
|[GetClassFromToken 方法](icordebugmodule-getclassfromtoken-method.md)|從中繼資料取得 ICorDebugClass。|  
|[GetEditAndContinueSnapshot 方法](icordebugmodule-geteditandcontinuesnapshot-method.md)|已取代。|  
|[GetFunctionFromRVA 方法](icordebugmodule-getfunctionfromrva-method.md)|未實作。|  
|[GetFunctionFromToken 方法](icordebugmodule-getfunctionfromtoken-method.md)|取得元資料標記所指定的函式。|  
|[GetGlobalVariableValue 方法](icordebugmodule-getglobalvariablevalue-method.md)|取得指定之全域變數的值物件。|  
|[GetMetaDataInterface 方法](icordebugmodule-getmetadatainterface-method.md)|取得中繼資料介面指標，可用來檢查模組的中繼資料。|  
|[GetName 方法](icordebugmodule-getname-method.md)|取得模組的檔案名。|  
|[GetProcess 方法](icordebugmodule-getprocess-method.md)|取得此模組的包含進程。|  
|[GetSize 方法](icordebugmodule-getsize-method.md)|取得模組的大小（以位元組為單位）。|  
|[GetToken 方法](icordebugmodule-gettoken-method.md)|取得此模組的資料表專案標記。|  
|[IsDynamic 方法](icordebugmodule-isdynamic-method.md)|指出模組是否為動態。|  
|[IsInMemory 方法](icordebugmodule-isinmemory-method.md)|指出此模組是否只存在於記憶體中。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
- [偵錯介面](debugging-interfaces.md)
