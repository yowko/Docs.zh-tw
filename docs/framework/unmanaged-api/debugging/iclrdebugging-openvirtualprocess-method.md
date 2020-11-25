---
title: ICLRDebugging::OpenVirtualProcess 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 2edd7f628e17c8dc6cbcbb577d06269ba8c64cb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723532"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess 方法

取得 ICorDebugProcess 介面，這個介面會對應至在進程中載入 (CLR) 模組的 common language runtime。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>參數  

 `moduleBaseAddress`  
 在目標進程中模組的基底位址。 如果指定的模組不是 CLR 模組，則會傳回 COR_E_NOT_CLR。  
  
 `pDataTarget`  
 在允許 managed 偵錯工具檢查進程狀態的資料目標抽象概念。 偵錯工具必須執行 [ICorDebugDataTarget](icordebugdatatarget-interface.md) 介面。 您應該執行 [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) 介面，以支援正在進行調試的 CLR 未安裝在本機電腦上的情況。  
  
 `pLibraryProvider`  
 在程式庫提供者回呼介面，可讓您視需要找出及載入特定版本的偵錯工具程式庫。 只有在或不是時，才需要這個參數 `ppProcess` `pFlags` `null` 。  
  
 `pMaxDebuggerSupportedVersion`  
 在此偵錯工具可以進行偵錯工具的最高 CLR 版本。 您應該從這個偵錯工具支援的最新 CLR 版本指定主要、次要和組建版本，然後將修訂編號設定為65535，以配合未來的就地 CLR 服務版本。  
  
 `riidProcess`  
 在要取得之 ICorDebugProcess 介面的識別碼。 目前，唯一接受的值為 IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2 和 IID_CORDEBUGPROCESS。  
  
 `ppProcess`  
 擴展所識別之 COM 介面的指標 `riidProcess` 。  
  
 `pVersion`  
 [in，out]CLR 的版本。 在輸入時，這個值可以是 `null` 。 它也可以指向 [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) 結構，在這種情況下，結構的 `wStructVersion` 欄位必須初始化為 0 (零) 。  
  
 在輸出時，傳回的 `CLR_DEBUGGING_VERSION` 結構將會填入 CLR 的版本資訊。  
  
 `pdwFlags`  
 擴展指定執行時間的相關資訊旗標。 如需旗標的描述，請參閱 [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) 主題。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pDataTarget` 為 `null`。|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)回呼傳回錯誤或未提供有效的控制碼。|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` 不會針對此版本的執行時間執行必要的資料目標介面。|  
|CORDBG_E_NOT_CLR|指出的模組不是 CLR 模組。 當無法偵測到 CLR 模組，因為記憶體已損毀、模組無法使用，或 CLR 版本晚于填充碼版本，也會傳回此 HRESULT。|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|此執行階段版本不支援此調試模型。 目前，CLR 版本不支援在 .NET Framework 4 之前的偵錯工具模型。 `pwszVersion`輸出參數在此錯誤之後仍設為正確的值。|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|CLR 的版本大於此偵錯工具所支援的版本。 `pwszVersion`輸出參數在此錯誤之後仍設為正確的值。|  
|E_NO_INTERFACE|`riidProcess`介面無法使用。|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|結構沒有可辨識的 `CLR_DEBUGGING_VERSION` 值 `wStructVersion` 。 目前唯一接受的值是0。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
