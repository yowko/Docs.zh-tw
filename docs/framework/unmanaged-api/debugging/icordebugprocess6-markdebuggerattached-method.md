---
title: "ICorDebugProcess6::MarkDebuggerAttached 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6d219e298e04157ea0670681c7550bd920bd284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached 方法
變更偵錯項目的內部狀態，讓 .NET Framework 類別庫中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法傳回 `true`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fIsAttached`  
 如果 `true` 方法應該指出已附加偵錯工具，則為 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>；否則為 `false`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下表所列的值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|`S_OK`|偵錯項目已成功更新。|  
|`CORDBG_E_MODULE_NOT_LOADED`|尚未載入包含 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法的組件，或遺漏中繼資料等其他一些錯誤導致無法辨認組件。<br /><br /> 這個錯誤很常見而且無害。 當其他組件載入時，您應該再次呼叫這個方法。|  
|其他失敗的 `HRESULT` 值。|可能表示偵錯工具或編譯器元件異常的其他值。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugProcess6 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
