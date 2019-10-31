---
title: ICorDebugObjectValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129757"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue 介面

"ICorDebugValue" 的子類別，表示包含物件的值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|取得此 `ICorDebugObjectValue` 參考之物件的 common language runtime （CLR） <xref:System.Type> 介面指標。|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|未實作。|  
|[GetFieldValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|取得[ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)的介面指標，表示指定類別之指定欄位的值。|  
|[GetManagedCopy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|已過時。 請勿呼叫此方法。|  
|[GetVirtualMethod 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|未實作。|  
|[IsValueClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|取得值，指出這個 `ICorDebugObjectValue` 所參考的物件是否為實值型別。|  
|[SetFromManagedCopy 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|已過時。 請勿呼叫此方法。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugObjectValue` 會維持有效，直到正在進行調試的進程繼續進行為止。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
