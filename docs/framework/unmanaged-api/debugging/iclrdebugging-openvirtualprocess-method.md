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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a313ea62455067fb36b94d942b0ce21589677e3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122573"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess 方法
取得對應至程序中載入 common language runtime (CLR) 模組 ICorDebugProcess 介面。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]目標處理序模組的基底位址。 如果指定的模組不是 CLR 模組，則會傳回 COR_E_NOT_CLR。  
  
 `pDataTarget`  
 [in]資料目標抽象概念，可讓 managed 偵錯工具來檢查處理狀態。 偵錯工具必須實作[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)介面。 您應該實作[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)介面，以支援案例所偵錯 CLR 未安裝在本機電腦。  
  
 `pLibraryProvider`  
 [in]程式庫提供者回呼介面，可讓特定版本的偵錯程式庫尋找並載入需求。 這個參數時才需要`ppProcess`或是`pFlags`不是`null`。  
  
 `pMaxDebuggerSupportedVersion`  
 [in]這個偵錯工具可以偵錯 CLR 最高的版本。 您應該指定主要、 次要和組建從這個偵錯工具支援，最新的 CLR 版本的版本，並設 65535 適應未來的就地 CLR 服務版本的修訂編號。  
  
 `riidProcess`  
 [in]要擷取的 ICorDebugProcess 介面識別碼。 目前，唯一接受的值是 IID_CORDEBUGPROCESS3、 IID_CORDEBUGPROCESS2 和 IID_CORDEBUGPROCESS。  
  
 `ppProcess`  
 [out]所識別的 COM 介面的指標`riidProcess`。  
  
 `pVersion`  
 [in、 out]CLR 版本。 輸入時，這個值可以是`null`。 它也可以指向[CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)結構，在此情況下的結構`wStructVersion`欄位必須初始化為 0 （零）。  
  
 在輸出時，傳回`CLR_DEBUGGING_VERSION`結構時會被填入 CLR 的版本資訊。  
  
 `pdwFlags`  
 [out]指定的執行階段的相關資訊的旗標。 請參閱[CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)旗標的說明主題。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_POINTER|`pDataTarget` 是`null`。|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)回呼會傳回錯誤，或未提供有效的控制代碼。|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` 未實作所需的資料目標介面，這個版本的執行階段。|  
|CORDBG_E_NOT_CLR|指定的模組不是 CLR 模組。 無法偵測到 CLR 模組，因為記憶體已損毀、 模組無法使用，或 CLR 版本晚於填充碼版本時，也會傳回此 HRESULT。|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|這個執行階段版本不支援此偵錯的模型。 偵錯模型目前不支援的 CLR 版本之前[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 `pwszVersion`輸出參數仍然發生此錯誤後設定為正確的值。|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|CLR 的版本大於宣告這個偵錯工具，以支援的版本。 `pwszVersion`輸出參數仍然發生此錯誤後設定為正確的值。|  
|E_NO_INTERFACE|`riidProcess`不提供介面。|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION`結構沒有可辨識的值`wStructVersion`。 此時唯一接受的值為 0。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
