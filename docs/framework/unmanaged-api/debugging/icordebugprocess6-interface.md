---
title: ICorDebugProcess6 介面
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c084042aa79170d46d179928956bd39a0731ddb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714915"
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6 介面
以邏輯方式擴充 ICorDebugProcess 介面，以啟用功能，例如解碼的編碼原生例外狀況偵錯事件，以及虛擬模組分割的 managed 偵錯事件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DecodeEvent 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|對已封裝在特殊設計之原生例外狀況偵錯事件承載中的 Managed 偵錯事件進行解碼。|  
|[EnableVirtualModuleSplitting 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|啟用或停用虛擬模組分割。|  
|[GetCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|取得特定程式碼位址之 Managed 程式碼的相關資訊。|  
|[GetExportStepInfo 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。|  
|[MarkDebuggerAttached 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|變更偵錯項目的內部狀態，讓 .NET Framework 類別庫中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法傳回 `true`。|  
|[ProcessStateChanged 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|會告知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序執行。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面僅適用於 .NET 原生。 嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
